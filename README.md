## Recomended texlive installation
Install texlive and required packages:
```bash
sudo apt-get install inkscape texlive texlive-bibtex-extra    \
texlive-generic-extra texlive-humanities texlive-latex-extra  \
texlive-math-extra texlive-publishers texlive-science         \
```

## Compilation
For compiling `LaTeX` you can use `scons`. Install it:
```bash
sudo apt-get install scons
```

You can compile all the PDFs under this folder simply by running:
```bash
scons && scons -c
```
