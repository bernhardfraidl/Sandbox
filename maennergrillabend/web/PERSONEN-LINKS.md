# Persönliche Links – Männergrillabend

Jede Person bekommt **ihren eigenen Link**. Beim Öffnen erkennt die Seite
automatisch, wer sie ist – **kein „Ich bin"-Auswählen mehr**, und **jeder
kann nur seine eigene Zeile bearbeiten**. Alle anderen sieht man nur.

## So funktioniert der Link

```
<DEINE-URL>?me=<TOKEN>
```

- `<DEINE-URL>` = die echte Web-Adresse der Seite. **Gibt es erst nach Stufe B**
  (Online-Stellen, z. B. GitHub Pages – siehe `BACKEND-SETUP.md`).
- `<TOKEN>` = der persönliche Code aus der Tabelle unten.

Beispiel (wenn die Seite später z. B. unter `https://bsf.github.io/grillabend/` liegt):

```
https://bsf.github.io/grillabend/?me=5rpq6g   ->  öffnet als „Bernhard"
```

## Die Tokens (stabil – nicht ändern)

| Person     | Token    | Link (Basis-URL ergänzen)          |
|------------|----------|------------------------------------|
| Bernhard   | `5rpq6g` | `<DEINE-URL>?me=5rpq6g`             |
| Martin W.  | `vjhpk8` | `<DEINE-URL>?me=vjhpk8`             |
| Alex       | `833vq4` | `<DEINE-URL>?me=833vq4`             |
| Ludwig     | `xx5ask` | `<DEINE-URL>?me=xx5ask`             |
| Martin F.  | `9y6zag` | `<DEINE-URL>?me=9y6zag`             |
| Dominik    | `64h7qh` | `<DEINE-URL>?me=64h7qh`             |
| Seraphin   | `yxfyvc` | `<DEINE-URL>?me=yxfyvc`             |
| Martin H.  | `qn4b2k` | `<DEINE-URL>?me=qn4b2k`             |
| Gerhard    | `jas8mv` | `<DEINE-URL>?me=jas8mv`             |

## Wichtig

- **Jeder kriegt nur seinen eigenen Link** (privat schicken, oder in der Gruppe
  als beschriftete Liste posten – „Bernhard → …, Martin W. → …").
- Die Tokens sind bewusst nicht erratbar, aber **keine echte Sicherheit** –
  wer den Link eines anderen hat, könnte dessen Zeile bearbeiten. Für eine
  Grillrunde unter Freunden reicht das. Echte Sperre = späteres Backend mit
  Login (nicht nötig für uns).
- Ohne `?me=…` (nur Basis-Link) erscheint wieder das Auswahlfeld – praktisch
  zum Ausprobieren.
