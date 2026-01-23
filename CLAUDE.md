# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Build Commands

Compile the resume (requires XeLaTeX and Biber):
```bash
xelatex resume.tex
biber resume
xelatex resume.tex
```

Single compilation (without bibliography updates):
```bash
xelatex resume.tex
```

## Architecture

This is a LaTeX resume using a custom `russell.cls` document class (derived from Awesome-CV template). It uses XeLaTeX for font handling and Biber for bibliography processing.

### Key Files

- **resume.tex**: Main document that imports all sections and configures personal info, colors, and margins
- **russell.cls**: Custom document class defining CV environments, styles, fonts, and bibliography formatting
- **cv/**: Section content files (education.tex, experience.tex, skills.tex, etc.)
- **fonts/**: Roboto and FontAwesome font files

### Document Structure

The main document uses `\input{}` to include section files from `cv/`. Sections can be enabled/disabled by commenting lines in resume.tex.

### CV Environments (defined in russell.cls)

- `\cventry{position}{title}{location}{date}{description}` - Work/education entries
- `\cvskill{category}{skills}` - Skills listing
- `\cvhonor{position}{title}{location}{date}` - Awards/honors
- `cvitems` environment - Bullet points within entries

### Style Customization

Colors and styles are configured in resume.tex by overriding defaults from russell.cls:
- Accent color: `\definecolor{russell}{HTML}{...}`
- Text styles: Override `\renewcommand*{\descriptionstyle}`, etc. in the preamble
- Margins: Configured via `\geometry{}`

### Font Dependencies

Requires fontspec-compatible engine (XeLaTeX/LuaLaTeX) with:
- Roboto font family (in fonts/)
- FontAwesome5 for icons
- Source Sans Pro (system or TeXLive)
