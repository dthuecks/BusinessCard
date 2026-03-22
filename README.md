# BusinessCard

Here are \LaTeX commands for six versions of a Washington College business card; three cards have a vertically-stacked college logo and three cards have a horizontal college logo.

I started from a business card template at https://andrewraim.github.io/software/latex-business-card, modifying commands to reflect my desired styles.

## Codespace setup

I installed \LaTeX using the following commands:
```
sudo apt update

sudo apt install texlive-full (recommended, not full, installation)

sudo apt install texlive-latex-extra texlive-fonts-recommended
```
I also installed LaTeX Workshop extension by James Yu.

Then, the codespace user settings file was modified to make XeLaTeX the default compiler (rather than pdfLaTeX which is the default). XeLaTeX was used as it is able to use .otf fonts, unlike pdflatex. You can make this change by opening the `settings.json` file by pressing shift+ctrl+P and typing `open user settings json`. Then, add the following code snippet inside the `{ }`:
```
"latex-workshop.latex.tools": [
    {
        "name": "xelatexmk",
        "command": "latexmk",
        "args": [
            "-xelatex",
            "-synctex=1",
            "-interaction=nonstopmode",
            "-file-line-error",
            "%DOC%"
        ]
    },
    // ... other tools can be kept or removed
],
"latex-workshop.latex.recipes": [
    {
        "name": "xelatexmk",
        "tools": [
            "xelatexmk"
        ]
    },
    // ... other recipes can be kept or removed
],
"latex-workshop.latex.recipe.default": "xelatexmk" // Set this to the new recipe name
```
Once this is done, you can run XeLaTeX on your .tex file to produce a pdf.