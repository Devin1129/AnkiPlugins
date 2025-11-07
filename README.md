# Keep model of add cards — Maintained Fork by Devin Yu

## 📘 Overview

This is a maintained fork of **“Keep model of add cards”**, originally created by **Arthur Milchior**.
It ensures that the note type (“model”) used in Anki’s *Add Cards* window does **not change automatically** when you edit or switch note types elsewhere, helping prevent data loss or accidental submissions under the wrong type.

---

## ✨ Changes in this fork (by Devin Yu)

This fork focuses on fixing initialization and cleanup issues introduced by recent Anki API changes.

* **Fixed broken hook wiring:**
  Updated `addCards.py` so the add-on properly defines and wires up `onResetSameModel`, ensuring the hook references a real method and the custom reset logic runs without crashing (`addCards.py`, lines 59–74).
* **Removed non-existent `_reject` override:**
  Replaced the obsolete `_reject` override with a new `_close` wrapper that safely removes the add-on’s hook when the *Add Cards* window closes (`addCards.py`, lines 77–82). This resolves the `AttributeError` on add-on load while still cleaning up state correctly.
* **Test recommendation:**
  Run Anki → reload the add-on → verify that “Keep model” adds cards without errors.

These fixes restore stability and compatibility with modern Anki versions (24.x and later).

---

## ⚙️ Usage

Once installed, this add-on locks the note type in each *Add Cards* window so it only changes when you explicitly choose a new model **from within that same window**.
It prevents unwanted model changes triggered by:

* Editing a note’s type in the Browser.
* Changing note type during import.
* Using the *Open multiple instances of the same window* add-on.

---

## 🧩 Technical Details

* Extends `aqt.addcards.AddCards` to intercept and override `setupChoosers`, `onReset`, and `_addCards`.
* Adds `onResetSameModel()` to preserve the current model selection.
* Implements a `ModelChooser` subclass to remove global model-change hooks.
* Now uses `_close` instead of `_reject` for cleanup.
* May conflict with other add-ons that heavily patch `aqt.addcards` or `ModelChooser`.

---

## 🔗 Original Project and Credits

| Key                     | Value                                                                                                                              |
| :---------------------- | :--------------------------------------------------------------------------------------------------------------------------------- |
| Original Author         | Arthur Milchior [arthur@milchior.fr](mailto:arthur@milchior.fr)                                                                    |
| Based on                | Anki code by Damien Elmes [anki@ichi2.net](mailto:anki@ichi2.net)                                                                  |
| Original Source         | [https://github.com/Arthur-Milchior/anki-keep-model-in-add-cards](https://github.com/Arthur-Milchior/anki-keep-model-in-add-cards) |
| Add-on Number           | [424778276](https://ankiweb.net/shared/info/424778276)                                                                             |
| Maintainer of this Fork | Devin Yu                                                                                                                           |
| License                 | GNU AGPL v3 or later — [https://www.gnu.org/licenses/agpl-3.0.html](https://www.gnu.org/licenses/agpl-3.0.html)                    |
| Fork Source             | [https://github.com/Devin-Yu/anki-keep-model-in-add-cards-fork](https://github.com/Devin-Yu/anki-keep-model-in-add-cards-fork)     |

**Support the original author:** [Ko-fi](https://Ko-fi.com/arthurmilchior) | [Patreon](https://www.patreon.com/bePatron?u=146206)

---

## 🪪 License (AGPL v3 or later)

This project is free software: you can redistribute it and/or modify it under the terms of the GNU Affero General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

You must preserve the above attributions and provide the complete corresponding source when distributing binary versions.
See the [`LICENSE`](./LICENSE) file for full details.

---

### ✅ Attribution Checklist

* Keep Arthur Milchior’s copyright and credits.
* Include the AGPL v3+ license text.
* Provide the full source code for your builds.
* Clearly state this is a maintained fork by Devin Yu.
* Link back to the original project.

--
