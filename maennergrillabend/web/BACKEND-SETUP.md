# Stufe B – Backend „alle sehen alle" (Vorbereitung)

Ziel: Alle Teilnehmer sehen **dieselben** Eintragungen (zentral gespeichert),
jeder bearbeitet weiterhin nur seine eigene Zeile (Stufe A ist schon fertig).

Dafür brauchen wir **zwei Dinge**:
1. einen kleinen **Datenspeicher (Backend)** – Empfehlung: **Supabase** (gratis),
2. die Seite **online** stellen – Empfehlung: **GitHub Pages** (gratis),
   damit es einen echten Link für die WhatsApp-Gruppe gibt.

> Der Code ist bereits vorbereitet: In `template.html` gibt es die
> Austauschpunkte `setStatus()`, `loadRemote()` und `onRemoteChange()`
> (mit `STUFE B:`-Kommentaren). Nur dort muss angesteckt werden.

---

## Schritt 1 – Supabase-Projekt (ca. 5 Min, gratis)

1. Auf https://supabase.com kostenlos registrieren → **New Project** anlegen.
2. Im Projekt **Project URL** und **anon public key** notieren
   (Settings → API). Der anon-Key darf öffentlich im Code stehen.
3. Im **SQL Editor** dieses Schema ausführen:

```sql
-- Verfügbarkeiten (eine Zeile je Person/Tag)
create table availability (
  day        date not null,
  person     text not null,
  status     text not null check (status in ('yes','maybe','no')),
  updated_at timestamptz not null default now(),
  primary key (day, person)
);

-- Fixer Termin / Gastgeber-Status (eine einzige Zeile)
create table settings (
  id         int primary key default 1,
  fixed_date date,
  updated_at timestamptz not null default now()
);
insert into settings (id) values (1) on conflict do nothing;

-- Realtime aktivieren, damit Änderungen live bei allen ankommen
alter publication supabase_realtime add table availability;

-- Einfachvariante: Lesen + Schreiben per anon-Key erlauben
alter table availability enable row level security;
create policy "read all"  on availability for select using (true);
create policy "write all" on availability for insert with check (true);
create policy "update all" on availability for update using (true);
```

> Optional härter (jeder nur seine Zeile): eigene Tabelle `tokens(token, person)`
> und Policies, die `person` gegen den mitgeschickten Token prüfen. Für uns
> nicht nötig.

---

## Schritt 2 – Code anstecken (in `template.html`)

Ganz oben im `<script>` Zugangsdaten setzen und Supabase-Client laden
(via `<script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2">`
im `<head>` der `index.html` – **nicht** in der Claude-Artifact-Version,
die blockt externe Skripte):

```js
const SB_URL = "https://DEINPROJEKT.supabase.co";
const SB_KEY = "DEIN-ANON-KEY";
const sb = supabase.createClient(SB_URL, SB_KEY);
```

Dann die drei Austauschpunkte füllen:

```js
// setStatus(): nach save() ergänzen
sb.from("availability").upsert({day:dateKey, person:personKey, status});
// (bei status "u" stattdessen: sb.from("availability").delete()
//    .match({day:dateKey, person:personKey}); )

// loadRemote(): beim Start alle Daten holen
async function loadRemote(){
  const {data} = await sb.from("availability").select("*");
  state.avail = {};
  (data||[]).forEach(r => {
    state.avail[r.day] = state.avail[r.day] || {};
    state.avail[r.day][r.person] = r.status;
  });
  renderAll();
}

// Live-Updates abonnieren
sb.channel("av").on("postgres_changes",
  {event:"*", schema:"public", table:"availability"},
  loadRemote).subscribe();
```

Im Init unten dann `loadRemote()` **statt** `seed()` aufrufen
(die Demo-Daten `seed()` fallen weg, sobald echte Daten kommen).

---

## Schritt 3 – Online stellen (GitHub Pages, gratis)

> Braucht **deine ausdrückliche Freigabe** (öffentliche Veröffentlichung).

1. Repo-Settings → **Pages** → Branch wählen (z. B. `main`), Ordner `/`.
2. Als Startseite `maennergrillabend/web/index.html` verwenden
   (oder Datei nach `index.html` ins Wurzelverzeichnis kopieren).
3. Ergebnis-URL (z. B. `https://<user>.github.io/<repo>/`) in
   `PERSONEN-LINKS.md` als `<DEINE-URL>` eintragen → fertige persönliche Links.

---

## Schritt 4 – Vorher noch klären
- **Steak-Foto lizenzieren** (aktuell iStock-Platzhalter mit Wasserzeichen)
  oder durch ein freies Bild ersetzen – **vor** dem Online-Stellen.
- Kurz Datenschutz bedenken: Namen + Verfügbarkeiten liegen dann bei Supabase
  (für eine Grillrunde unkritisch, aber gut zu wissen).
