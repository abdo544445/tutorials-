Using LaTeX on Fedora with an IDE involves several steps, from installing the necessary software to configuring your IDE and compiling your documents into PDFs. Here’s a step-by-step guide to get you started:

### 1. Install LaTeX Distribution

First, you need to install a LaTeX distribution. The most common and comprehensive one is TeX Live.

Open a terminal and run:
```bash
sudo dnf install texlive-scheme-full
```
This command installs the full TeX Live distribution, which includes all the necessary packages and tools for LaTeX.

### 2. Install an IDE for LaTeX

There are several IDEs for LaTeX, but some popular ones include TeXstudio, Overleaf (web-based), and Visual Studio Code with LaTeX extensions. Here, we'll cover TeXstudio and Visual Studio Code.

#### TeXstudio

To install TeXstudio, run:
```bash
sudo dnf install texstudio
```

#### Visual Studio Code

For Visual Studio Code, you’ll need to install VS Code and the LaTeX Workshop extension.

First, install VS Code:
```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo sh -c 'echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ntype=rpm-md\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/vscode.repo'
sudo dnf check-update
sudo dnf install code
```

Next, open VS Code and install the LaTeX Workshop extension:
1. Open VS Code.
2. Go to the Extensions view by clicking on the Extensions icon in the Activity Bar on the side of the window or by pressing `Ctrl+Shift+X`.
3. Search for "LaTeX Workshop" and install it.

### 3. Configure Your IDE

#### TeXstudio

1. Open TeXstudio.
2. Go to `Options` > `Configure TeXstudio`.
3. Under the `Build` tab, ensure that the default compiler is set to `pdflatex` (or another compiler of your choice, such as `xelatex` or `lualatex`).
4. You can also customize other settings like the editor, spell check, and preview options according to your preferences.

#### Visual Studio Code

1. Open VS Code.
2. Open the Command Palette by pressing `Ctrl+Shift+P` and search for `Preferences: Open Settings (JSON)`.
3. Add the following configuration to your `settings.json` file:
   ```json
   {
       "latex-workshop.latex.tools": [
           {
               "name": "pdflatex",
               "command": "pdflatex",
               "args": [
                   "-synctex=1",
                   "-interaction=nonstopmode",
                   "-file-line-error",
                   "%DOC%"
               ]
           }
       ],
       "latex-workshop.latex.recipes": [
           {
               "name": "pdflatex",
               "tools": [
                   "pdflatex"
               ]
           }
       ],
       "latex-workshop.view.pdf.viewer": "tab",
       "latex-workshop.synctex.synctexjs.enabled": true
   }
   ```

### 4. Create and Compile a LaTeX Document

Create a new LaTeX document with the following content as an example:

```latex
\documentclass{article}
\begin{document}
Hello, World!
\end{document}
```

#### Compiling in TeXstudio

1. Save the file with a `.tex` extension.
2. Click the green arrow (Compile) button in the toolbar or press `F5` to compile the document.
3. The compiled PDF will appear in the built-in viewer.

#### Compiling in Visual Studio Code

1. Save the file with a `.tex` extension.
2. Open the Command Palette by pressing `Ctrl+Shift+P` and search for `LaTeX Workshop: Build LaTeX project`.
3. Select the recipe (e.g., `pdflatex`) to compile the document.
4. The compiled PDF will open in a new tab in VS Code.

### 5. Final Touches

To ensure your documents have a polished and professional appearance, consider the following:

- **Packages**: Use additional packages to enhance the functionality and appearance of your document, such as `amsmath` for advanced mathematics, `graphicx` for including images, and `hyperref` for hyperlinks.
- **Bibliography**: Use `biblatex` or `natbib` for managing references and citations.
- **Formatting**: Customize your document’s formatting by defining styles, margins, headers, and footers.

### Example of a More Complex Document

Here is an example with some additional packages and settings:

```latex
\documentclass{article}
\usepackage[utf8]{inputenc}
\usepackage{amsmath}
\usepackage{graphicx}
\usepackage{hyperref}
\usepackage{geometry}
\geometry{a4paper, margin=1in}

\title{Sample Document}
\author{Your Name}
\date{\today}

\begin{document}

\maketitle

\section{Introduction}
This is a sample document to demonstrate LaTeX on Fedora with an IDE.

\section{Mathematics}
Here is an example of an equation:
\begin{equation}
    E = mc^2
\end{equation}

\section{Images}
\begin{figure}[h]
    \centering
    \includegraphics[width=0.5\textwidth]{example-image}
    \caption{An example image.}
    \label{fig:example}
\end{figure}

\section{References}
You can add references using \texttt{biblatex} or \texttt{natbib}.

\end{document}
```

By following these steps, you will be able to use LaTeX effectively on Fedora with your preferred IDE and produce polished PDFs for your documents.
