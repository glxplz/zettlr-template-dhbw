# Installation

Open a terminal in the location where you want to create your project and clone the repository

```bash
git clone https://github.com/glxplz/zettlr-template-dhbw.git
```

Open Zettlr and navigate to **File -> Open Workspace**

<img src="./readme-screenshots/image-20210423192358174.png" alt="image-20210423192358174" style="zoom:33%;" />

Select the folder you just cloned

Expand the workplace in Zettlr

<img src="./readme-screenshots/image-20210423192827956.png" alt="image-20210423192827956" style="zoom:33%;" />



Right click **Export** and go to project settings

<img src="./readme-screenshots/image-20210423193158650.png" alt="image-20210423193158650" style="zoom:33%;" />

Under **Custom TeX-Template** select the "**main.tex"** in the project's parent folder **(if you move you project folder, you will have to redo this step!)**

<img src="./readme-screenshots/image-20210423193414869.png" alt="image-20210423193414869" style="zoom:67%;" />

<img src="./readme-screenshots/image-20210423193458996.png" alt="image-20210423193458996" style="zoom:67%;" />

In **Project settings** you may change other attributes of your project like title, author, margins, citation styles etc.

## Adding support for [pandoc-crossref](http://lierdakil.github.io/pandoc-crossref/)
Next we will have to change Zettlr's default export command to make cross references (referencing of figures and sections) work.
Press **Ctrl**+**,** to open settings. Go to "Advanced" and replace the Pandoc command with the following
```
pandoc -F pandoc-crossref "$infile$" -f markdown $outflag$ $tpl$ $toc$ $tocdepth$ $bibliography$ $cslstyle$ $standalone$ --pdf-engine=xelatex --mathjax -o "$outfile$" --number-sections --listings
```

## Adding [Mermaid](https://mermaid-js.github.io/mermaid/#/) Support
```bash
npm install -g mermaid-filter
```
and add `-F mermaid-filter` to the Advanced Settings pandoc command.

## Linking a BibTex database
Citation databases are supported in CSL JSON or BibTex (.bib) formats. These can be exported from or linked to citation tools such as Zotero.
To link your database go to **Settings -> Export -> Citation Database** and select the file you want to use. Citations may now be added using **'@'**.

# Exporting a PDF

Right click the project folder and click **Export Project**

<img src="./readme-screenshots/image-20210423194222698.png" alt="image-20210423194222698" style="zoom:33%;" />

**This may take a while! If you didn't get a success or error notification it is still running!**
See also:
https://docs.zettlr.com/en/core/export/
https://docs.zettlr.com/en/academic/projects/

# Common Errors

## Export failed - The font "XYZ" cannot be found

Go to **Project settings** and under **Font** select fonts which are installed on your system. Hit **Save**. The name has to match exactly.

# Changing stuff in the template

## I want to change the language

In **ads/settings.tex** change the line 
```tex
\newcommand{\documentLanguage}{de}
```
to your desired language ("de" for German or "en" for English)
g.
## I want to change the document type

In **ads/settings.tex** change the line 

```tex
\newcommand{\documentType}{T2\_3000}
```

to your desired type. Possible types are

```tex
T2\_1000
T2\_2000
T2\_3000
T2\_3100
T2\_3300
```

## I want to change something else

You can find everything you will need in **ads/settings.tex**. The following lines can be used for configuration and should be self explanatory:

`````tex
\newcommand{\documentPeriod}{12 Wochen}

\newcommand{\matriculationNumber}{12345678}

\newcommand{\locationUniversity}{Friedrichshafen}
\newcommand{\department}{Wirtschatsingenieurwesen - Maschinenbau}
\newcommand{\course}{TWI18-1}

\newcommand{\degree}{Bachelor of Engineering}

\newcommand{\releaseDate}{März 2021}
\newcommand{\releaseLocation}{Manching}

\newcommand{\companyName}{Airbus Defence and Space GmbH}
\newcommand{\companyLocation}{Manching}

\newcommand{\tutor}{Dr.-Ing. Peter Lustig}
`````

## I don't need a list of tables/list of figures/listings

In **references.md** remove the relevant lines:

`````tex
\pagebreak
\listoftables
\pagebreak
\listoffigures
\pagebreak
\addcontentsline{toc}{section}{\lstlistlistingname}
\lstlistoflistings
\pagebreak
`````

## I want a specific citation style
You can specify a citation style through a CSL file in **Project settings -> CSL-Style**. CSL style files for all common style can be found here:

https://github.com/citation-style-language/styles

# Acknowledgements
This project contains parts of Stefan Schneides [DHBW-Latex template](https://github.com/schnes4/dhbw-heidenheim-latex-template). Thank you!
