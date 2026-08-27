# Codebase Analysis: Screenshots-to-PPTX Generator

## 1. Executive Summary
- **Purpose**: Zero-config automated tool converting folders of screenshots into structured, 16:9 widescreen PowerPoint (`.pptx`) presentations.
- **Entrypoint**: `create_pptx.py` (with PEP 723 script metadata and `pyproject.toml` support).
- **Core Dependencies**: `python-pptx`, `pillow`.

## 2. Architecture & Modules
- **Engine (`create_pptx.py`)**:
  - Natural sorting (`natural_sort_key`) for sequential screenshot numbering (`1.png`, `2.png`, `10.png`).
  - Title parsing (`clean_title`) with automatic "Slide X" detection and slug cleanup.
  - Cover slide creation: 16:9 layout (`13.333" x 7.5"`), Slate/Royal Blue styling, breadcrumb subtitle.
  - Content slide generation: Dynamic aspect-ratio-preserving scaling, margin bounds, slide headers (`Slide X of Y - filename.png`).
  - Directory batch scanner: Scans root directory for image subdirectories, ignores dotfiles/submodules, outputs corresponding `<folder_name>.pptx`.

## 3. Tooling & Environment
- **Package Manager**: `uv` (`uv run create_pptx.py`).
- **Dependencies**: Managed via `pyproject.toml` & inline PEP 723 script block.
- **Submodule**: `autonomous-coding-agents` (READ-ONLY inem flywheel framework).

## 4. Current Gaps & Opportunities
- **Test Suite**: No automated unit/integration test suite (`tests/test_create_pptx.py`) verifying slide dimensions, shape counts, aspect ratio preservation, and image format coverage.
- **CLI Flags / Config**: Hardcoded root scanning without optional arguments for custom source/target directories, custom themes/colors, or title overrides.
- **Error Handling**: Graceful recovery for corrupted image files or permission errors during file write.
