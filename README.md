# Nil Ruz · Projects

Flutter & mobile developer from Barcelona. This is where I show what I build.
More projects coming soon.

---

## 🗂️ Buscador de duplicados

**A Windows desktop app that finds exact duplicate files and visually similar photos, and cleans them up without ever touching your originals.**

[![Repo](https://img.shields.io/badge/GitHub-buscador--de--duplicados-181717?logo=github)](https://github.com/Sayessol/buscador-de-duplicados)
![Python](https://img.shields.io/badge/Python-3.12-3776AB?logo=python&logoColor=white)
![Tests](https://img.shields.io/badge/tests-128%20passing-brightgreen)
![License](https://img.shields.io/badge/license-MIT-blue)

### The problem
Years of backups and phone transfers leave folders full of the same files and near-identical photos. Most cleaners delete things straight away, which is risky. This one is built around one rule: **nothing is deleted without confirmation, and every move can be undone.**

### What it does
| Tab | What it does |
|---|---|
| **Exact duplicates** | Finds byte-identical files regardless of name, shows previews and picks a main copy. |
| **Similar photos** | Groups recompressed, downscaled or filtered versions of the same photo and keeps the best quality one. |
| **Gather images** | Moves or copies photos scattered across subfolders into a single folder. |

Also: simple and advanced modes, history with undo, image viewer with zoom, light/dark/auto theme, filters by category, extension, name, folder and size.

### How it works
- **Exact duplicates in three passes.** Group by size, then hash the first 64 KB (BLAKE2b), then hash the full file only for the remaining candidates. In my benchmark it read about **34% of the data** that hashing everything would, and found the same 386 groups.
- **Similar photos with perceptual hashing.** A 64-bit dHash plus a 4×4 colour signature, a BK-tree over Hamming distance to avoid comparing every pair, and Union-Find to link groups.
- **Responsive UI.** Heavy work runs in a background thread and talks to the interface through a queue, so the window never freezes.
- **Clean separation.** Logic lives in `core/`, the interface in `ui/`.

### Quality
- 128 automated tests with pytest: **93% coverage on the core**, 79% on the interface
- Linting with ruff and type checking with mypy
- GitHub Actions runs the tests on every push
- Distributed as a single `.exe` and a portable ZIP, built with PyInstaller

### Known limits
Windows only. It does not detect cropped or rotated photos, and it cannot read phones connected over USB (MTP/PTP).

### Stack
`Python 3.12` `CustomTkinter` `Pillow` `pytest` `ruff` `mypy` `GitHub Actions` `PyInstaller`

### Try it
Download the `.exe` or the portable ZIP from [Releases](https://github.com/Sayessol/buscador-de-duplicados/releases), or run it from source:
```bash
pip install -r requirements.txt
python app.py
```

### How I built it
It started as a 150-line script and grew into a tested, packaged app. I built it with Claude as a coding assistant: I defined the requirements, the safety rules and the architecture, and used AI to speed up the implementation, with tests to check the result.

---

## 🔜 Coming next

- 🎮 Unity mini-games (2D, AR and VR)
- 📱 Flutter showcase app (Clean Architecture + Riverpod)

---

## 🛠️ Tech I work with

`Flutter` `Dart` `Riverpod` `Clean Architecture` `REST` `Firebase` `WebSockets` `Python` `Unity` `Java` `SQL` `Git`

## 📬 Contact

[LinkedIn](https://www.linkedin.com/in/nilruz) · nilruznra@gmail.com
