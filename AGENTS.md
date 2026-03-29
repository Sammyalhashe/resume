# AGENTS.md

## Building the Resume

```bash
nix build
# Output: result/resume.pdf
```

The resume is compiled with pdflatex via `latexmk` inside a Nix derivation. See `flake.nix` for texlive dependencies.

## File Structure

```
resume.tex          # Main file: preamble + \input{} calls
sections/
  header.tex        # Name, contact info
  skills.tex        # Technical Skills section
  experience.tex    # Work Experience section
  projects.tex      # Projects section
  education.tex     # Education section
  awards.tex        # Awards section
```

## Template Macros (jakegut/sb2nov)

### Work Experience

```latex
\resumeSubheading
  {Company}{Date Range}
  {Job Title}{Location}
  \resumeItemListStart
    \resumeItem{Bullet point describing what you did and impact.}
    \resumeItem{Use \textbf{bold} for technologies and key terms.}
  \resumeItemListEnd
```

### Projects

```latex
\resumeProjectHeading
  {Project Name $|$ \textbf{Tech Stack}}
  {Date or Status}
  \resumeItemListStart
    \resumeItem{Description with measurable outcomes when possible.}
  \resumeItemListEnd
```

### Nested Sub-items (e.g., for detailed sub-bullets under a work item)

```latex
\resumeItem{Main achievement that has sub-details.}
  \begin{itemize}[leftmargin=0.3in]
    \item\small{Sub-detail one.}
    \item\small{Sub-detail two.}
  \end{itemize}
  \vspace{-4pt}
```

### Skills Section

```latex
\begin{itemize}[leftmargin=0.15in, label={}]
  \small{\item{
    \textbf{Category}{: item1, item2, item3} \\
  }}
\end{itemize}
```

## Links and URLs

```latex
% Email
\href{mailto:sammy@salh.xyz}{\underline{sammy@salh.xyz}}

% Regular URL
\href{https://github.com/Sammyalhashe}{\underline{github.com/Sammyalhashe}}
```

## Adding/Editing Content

1. Open the relevant file in `sections/`
2. Make your changes
3. Stage files: `git add sections/<file>.tex resume.tex`
4. Build: `nix build`
5. View: `firefox result/resume.pdf` or convert to PNG

## Build Workflow

```bash
# Always stage changes before building (nix build uses git-tracked files)
git add sections/ resume.tex

# Build
nix build

# Check the output
mutool info result/resume.pdf           # page count, fonts
mutool draw -F txt result/resume.pdf    # extract text

# Quick visual check (combine pages side by side)
cp result/resume.pdf /tmp/resume.pdf
mutool convert -o /tmp/p%d.png -O resolution=200 /tmp/resume.pdf
convert \( /tmp/p1.png /tmp/p2.png +append \) -bordercolor white -border 20 /tmp/view.png
firefox /tmp/view.png &
```

## Troubleshooting

### Font errors (tcrm1000, T1 encoding)
- Ensure `\usepackage{lmodern}` is in the preamble
- Ensure `lmodern` is listed in `flake.nix` texlive packages
- Do NOT use `\scshape` (small caps) - requires T1 fonts not in scheme-small

### `hrefmailto` not recognized
- Use `\href{mailto:email}{display text}` instead of `\hrefmailto{}{}`

### New files not included in build
- `nix build` uses `src = self` which only copies git-tracked files
- Run `git add <newfile>` before building

### Overfull/underfull hbox warnings
- These are usually cosmetic (text slightly exceeds line width)
- Check with: `nix log $(nix-store --query --deriver result) | grep -i overfull`

## Design Principles

- **Format**: Single-column, ATS-friendly, no tables/columns that confuse parsers
- **Length**: 2 pages is acceptable for 6+ years experience
- **Style**: Action-verb-first bullets, measurable outcomes, bold key technologies
- **Fonts**: Latin Modern (via lmodern package), 11pt, letter paper
- **Margins**: 0.5in

## Adding New Packages

If you need a LaTeX package not in `scheme-small`, add it to `flake.nix`:

```nix
inherit (pkgs.texlive) scheme-small latexmk titlesec enumitem lmodern newpackage;
```

To find available packages: search [CTAN](https://ctan.org/search) then check if it exists in nixpkgs texlive.
