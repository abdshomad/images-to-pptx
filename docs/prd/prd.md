# Product Requirements Document (PRD): Screenshots-to-PPTX Generator

## 1. Overview & Vision
A zero-config, highly-automated CLI tool that transforms folders of sequentially named screenshots into cleanly styled, professional 16:9 widescreen PowerPoint (`.pptx`) decks for technical walkthroughs, tutorials, and documentation.

## 2. Core Functional Requirements

### 2.1 Module 1: Core Presentation Engine & Slide Formatting
- **Slide Dimensions**: Native 16:9 widescreen format (`13.333" x 7.5"`).
- **Cover / Title Slide**:
  - Automatically generated hero slide displaying folder title formatted in Title Case.
  - Accent bar (Royal Blue 600) and Slate typography (`Segoe UI`).
  - Total slide count summary metadata subtitle.
- **Content Slides**:
  - Header: Left accent pill, formatted title (`clean_title`), and breadcrumb subtitle (`Slide X of Y - filename.ext`).
  - Image Placement: Dynamic aspect-ratio-preserving centering without distortion or border clipping.
  - Natural Ordering: Numeric sorting handling multi-digit sequences (`1.png`, `2.png`, `10.png`).
  - Supported Formats: `.png`, `.jpg`, `.jpeg`, `.webp`, `.bmp`, `.gif`, `.tiff`.

### 2.2 Module 2: CLI Interface & Directory Batching
- **Default Execution**: Zero-arg batch run scanning all top-level subdirectories in working directory (`uv run create_pptx.py`).
- **Configurable Arguments**:
  - Optional `--input` / `-i` to target a single folder or specific parent directory.
  - Optional `--output` / `-o` to customize destination folder.
  - Optional `--widescreen` / `--standard` aspect ratio toggles (default `16:9`).
- **Safety**: Ignore dotfiles (`.git`, `.venv`), ignore submodules, and handle empty/non-image folders gracefully.

### 2.3 Module 3: Test Suite & Verification Framework
- **Automated Tests (`pytest`)**:
  - Test natural sort algorithm across various naming schemes (`1.png`, `step-02.jpg`, `img10.png`).
  - Test slide dimensions (`13.333" x 7.5"`), shape hierarchies, and placeholder count.
  - Test image aspect ratio calculations for landscape, portrait, and square screenshots.
  - Test CLI invocation and output file generation with mock image directories.
- **Quality Gates**: Maintain ≤256 LOC per file, zero external runtime setup beyond `uv`.

## 3. Success Metrics
- 1-command zero-config conversion (`uv run create_pptx.py`).
- 100% green test suite on `pytest`.
- 100% compliance with file size limits (≤256 LOC per file).
