# Keep model of add cards — Maintained Fork by Devin Yu

## 📘 Overview

This is a maintained fork of **“Keep model of add cards”** originally created by **Arthur Milchior**.
It ensures that the note type (“model”) used in Anki’s *Add Cards* window does **not change automatically** when you edit or switch note types elsewhere.
This behavior helps prevent data loss and unintended submissions under the wrong note type.

### ✨ Changes in this fork (by Devin Yu)

* Updated for Anki 24.x API changes.
* Fixed compatibility with other add-ons modifying `aqt.addcards` and `ModelChooser`.
* Improved stability when multiple “Add Cards” windows are open.
* Refactored initialization hooks and reset logic.
* Updated README and metadata for clarity and licensing.

---

## ⚙️ Usage

Once installed, this add-on locks the note type in each “Add Cards” window so it only changes when explicitly chosen **from within that same window**.
It prevents unwanted model changes triggered by:

* Editing a note’s type in the Browser.
* Changing note type during import.
* Using the *Open multiple instances of the same window* add-on.

---

## 🧩 Technical Details

* Extends `aqt.addcards.AddCards` class to intercept and override `setupChoosers`, `onReset`, and `_addCards`.
* Adds `onResetSameModel()` method to preserve current model selection.
* Re-implements `ModelChooser` subclass to remove global model-change hooks.
* May conflict with other add-ons that deeply patch these classes.

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

### ✅ Summary of Attribution and Compliance Requirements

* Keep Arthur Milchior’s copyright and credits.
* Include the AGPL v3+ license text.
* Provide the full source code for your builds.
* Clearly state that this is a maintained fork by Devin Yu.
* Link back to the original project.
