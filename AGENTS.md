# AGENTS.md - Quantum Entanglement Visualization Survey

## Project Overview

This is a LaTeX-based academic literature survey paper on quantum entanglement visualization. The main document is `quantum-entanglement-visualization-survey.tex`.

## Build Commands

### Compile PDF
```bash
pdflatex quantum-entanglement-visualization-survey
bibtex quantum-entanglement-visualization-survey
pdflatex quantum-entanglement-visualization-survey
pdflatex quantum-entanglement-visualization-survey
```

### Using latexmk (automatic)
```bash
latexmk -pdf quantum-entanglement-visualization-survey
```

### Clean build artifacts
```bash
latexmk -C
```

### View PDF
```bash
xdg-open quantum-entanglement-visualization-survey.pdf
```

## LaTeX Code Style Guidelines

### Document Structure
- Use semantic sectioning: `\section{}`, `\subsection{}`, `\subsubsection{}`
- Always label sections: `\section{Name}\label{sec:name}`
- Use `\cref{}` (cleveref) for cross-references, never hardcoded section numbers
- Use `\cite{}` for citations, maintain consistent citation style via natbib

### Packages and Imports
- Load packages in preamble only
- Preferred packages: amsmath, amssymb, physics, tcolorbox, enumitem, cleveref
- Avoid redundant package loading

### Math and Equations
- Use `align` environments for multi-line equations (not `eqnarray`)
- Prefer `\text{}` over `\mbox{}` for inline text in math
- Number equations selectively with `\tag{}` if needed
- Use `\ket{}`, `\bra{}`, `\braket{}` from physics package

### Figures and Tables
- Use `\begin{figure}[htbp]` for placement (h=here, t=top, b=bottom, p=page)
- Always include `\label{fig:...}` after caption
- Use `\cref{}` for references
- Tables: use booktabs package, avoid vertical rules

### Labels and References
- Prefix labels: `sec:`, `fig:`, `tab:`, `eq:`, `thm:`, `def:`
- Use descriptive names: `sec:geometric` not `sec:1`
- Always use `\cref{}` (cleveref) for automatic type insertion

### Bibliography
- Use BibTeX with natbib: `\bibliographystyle{plainnat}`
- Keep references in .bib file
- Use consistent citation commands: `\cite{}` or `\textcite{}`

### Formatting Conventions
- Use 2 spaces for indentation (LaTeX convention)
- Maximum line length: 80 characters
- Blank line between paragraphs
- No trailing whitespace
- Use `\bigskip`, `\smallskip` for spacing, not hardcoded vertical space

### Naming Conventions
- File names: lowercase with hyphens (e.g., `quantum-entanglement-visualization-survey.tex`)
- Labels: descriptive, lowercase with colons (e.g., `\label{fig:bloch-sphere}`)

### Error Handling
- Always check .log file for warnings/errors after compilation
- Fix overfull/underfull hbox warnings
- Address undefined references (run pdflatex twice)
- Check for multiply-defined labels

## Git Workflow

- Commit meaningful messages describing content changes
- Do not commit compiled PDFs or build artifacts
- Backup files (`.bak*`) can be ignored

## Project Files

- Main: `quantum-entanglement-visualization-survey.tex`
- PDF output: `quantum-entanglement-visualization-survey.pdf`
- Backup files: `quantum-entanglement-visualization-survey.bak*`
- Auxiliary: `.aux`, `.toc`, `.log`, `.out`, `.fls`

## Validation and Quality Checks

### PDF Compilation Check
Always verify the PDF compiles without errors:
```bash
latexmk -pdf quantum-entanglement-visualization-survey
```

### Reference Validation
- Run pdflatex twice to ensure all cross-references resolve
- Check .log file for "Warning: Reference `X` on page Y undefined"
- Verify all \cref{} references display correctly (e.g., "Figure 1", "Section 2.1")

### Bibliography Check
- Ensure .bib file entries are complete and properly formatted
- Run bibtex then pdflatex twice to resolve citations
- Check .log for "Citation `X` on page Y undefined"

### Spell Checking (Optional)
```bash
aspell -c quantum-entanglement-visualization-survey.tex
```

### Grammar and Style (Optional)
```bash
texcount quantum-entanglement-visualization-survey.tex
```

## Additional LaTeX Conventions

### List Environments
- Use `itemize` for bullet lists, `enumerate` for numbered lists
- Customize with enumitem package: `\begin{enumerate}[label=(\roman*)]`
- Use descriptive labels: `\begin{enumerate}[label=\textbf{Step \roman*:}]`

### Tcolorbox for Theorems/Lemmas
```latex
\tcolorboxenvironment{section}{
  colback=red!5!white,
  colframe=red!75!black,
  fonttitle=\bfseries
}
```

### Hyperlinks and URLs
- Use `\href{url}{text}` for clickable links
- Use `\url{url}` for displaying URLs
- Avoid bare URLs in text

### Citations
- Use `\cite{key}` for inline citations
- Use `\textcite{key}` for author-year style (with natbib)
- Group multiple citations: `\cite{key1,key2,key3}`

### Equations in Text
- Use `$...$` for inline math, never `\(...\)`
- Use `\[...\]` for display math, never `$$...$$`
- Prefer `align` over `eqnarray` for multi-line equations
- Add `\!` for negative thin space in expressions like `$\ket{0}\! \ket{1}$`

### Figures and Graphics
- Place figures in dedicated directory (e.g., `figures/`)
- Use `\graphicspath{{figures/}}` in preamble
- Supported formats: .pdf (preferred), .png, .jpg
- Always specify width with `\includegraphics[width=0.8\textwidth]{...}`

### Tables
- Use booktabs: `\toprule`, `\midrule`, `\bottomrule`
- Avoid vertical lines; use horizontal only
- Caption above tables: `\caption{...}\label{tab:...}`
- Reference with `\cref{tab:...}`

### Cross-Reference Best Practices
- Always label sections, figures, tables, equations
- Place \label immediately after \caption or section title
- Use meaningful label names: `\label{fig:majorana-constellation}`
- Reference with \cref (not \ref) for automatic type insertion

### Acronyms and Abbreviations
- Define on first use: "quantum entanglement (QE)"
- Consider glossary package for extensive terminology
- Use `\textit{...}` for emphasized terms in math mode

### File Organization
- Keep main document in root directory
- Place figures in `figures/` subdirectory
- Use separate .tex files for chapters: `\input{chapter1.tex}`
- Maintain consistent file naming: lowercase, hyphens

### Version Control
- Track .tex source files only
- Add to .gitignore:
  ```
  *.pdf
  *.aux
  *.log
  *.out
  *.toc
  *.bbl
  *.blg
  *.bak*
  ```
- Commit source files, not compiled output

### Collaboration
- Use consistent line endings (LF)
- Maximum line length: 80 characters
- Use comments sparingly: `% Section: Geometric Methods`
- Avoid binary files in repository