README FOR pdfannotations PACKAGE
=================================

Version: 2.3
Date: 2023-11-10

Overview
--------
pdfannotations is a LaTeX package designed for annotating PDF slides with LaTeX elements, adding interludes, and including code snippets. It offers a flexible way to enhance PDF presentation slides with additional LaTeX content. The package utilizes LaTeX3 syntax and requires the pdfLaTeX compiler.

Features and Usage
------------------
The pdfannotations package includes the following commands and environments:

1. slideannotate: 
   - Syntax: \begin{slideannotate}{PDF Number-Slide Number} ... \end{slideannotate}
   - Allows annotations directly onto PDF slides.
   - Supports math and LaTeX markup.
   - Limitation: Content does not extend to multiple pages.

2. slideinterlude:
   - Syntax: \begin{slideinterlude}{PDF Number-Slide Number} ... \end{slideinterlude}
   - Inserts interludes between slides for additional content.
   - Supports math, LaTeX markup, and programming code.
   - For short code snippets, {verbatim} can be used.

3. \annotatepdf:
   - Syntax: \annotatepdf{PDF Number}
   - Invokes the annotation process for a specified PDF.

4. \labelgraphics:
   - Syntax: \labelgraphics[options]{filename}
   - Includes graphics with filename labels.

5. \suppressslide:
   - Syntax: \suppressslide{PDF Number-Slide Number}
   - Suppresses specific slides.

6. \includecode:
   - Syntax: \includecode[options]{filename}
   - Includes external code with syntax highlighting.
   - Auto-detects language formatting by file extension.
   - {verbatim} recommended for short snippets within {slideinterlude}.

7. \listpdfs:
   - Lists all PDFs and their index numbers as specified in the user configuration.

User Configuration
------------------
Customize document metadata and settings by modifying the variables in the user configuration section at the top of the package code.

Known Limitations
-----------------
- {slideannotate} environment does not span multiple pages.
- {verbatim} and {lstlisting} not supported within {slideannotate}.
- {verbatim} usable within {slideinterlude} for short code snippets.

System Requirements
-------------------
- LaTeX3 syntax.
- pdfLaTeX compiler.

Successfully Tested With Packages
---------------------------------
- {mathtools}
- {cancel}
- {booktabs}
- {array}
- {longtable}
- {mathrsfs}
- {mathtools}

Minimal Example
---------------
\documentclass{article}
\usepackage{pdfannotations}

\begin{document}

\begin{slideannotate}{1-2}
Annotation for slide 2 of the first PDF.
\end{slideannotate}

\begin{slideinterlude}{1-3}
Interlude with \LaTeX{} markup and math like \( E = mc^2 \).
\includecode{example.py}
\end{slideinterlude}

\annotatepdf{1}
\listpdfs

\end{document}
(Replace "example.py" with a real file path.)

GitHub Repository: https://github.com/chevannanayakkara/pdfannotations

License
-------
Free with no warranty under the LaTeX Project Public License (LPPL) version 1.3c.

Note: This README complements the full documentation available on GitHub.

Changelog
---------
Version 2.3 (2023-11-10):
- Brought all user-specified variables to the top of the preamble for easier customization.
- Added \listpdfs command to list all PDFs and their index numbers.

Version 2.2.3 (2023-11-08):
- Added packages booktabs and longtable for table environment support.
- Reformatted the entire document for improved readability and structure.

Version 2.2.2 (2023-11-07):
- Removed the changelog from the code to be included in the README file instead.

Previous updates:

Version 2.2.1 (2023-11-06):
- Modified when \clearpage is invoked to make slide transitions more natural.

Version 2.2:
- Moved title, author, and date to user-specified variables.
- Ensured that full text is used without stripping spaces.
- Reorganized the code and added comments to sections for clarity.

Version 2.1:
- Added syntax highlighting and line numbers for included Python code blocks.
- Language formatting is auto-detected by the included file's extension.

Version 2.0:
- Added functionality to include multi-line code from an external file into the {slideinterlude} environment.

Version 1.9.1:
- Fixed a bug in \labelgraphics where the interlude format was not preserved.

Version 1.9:
- Introduced \suppressslide{x

-y} command to exclude specific slides from being displayed.

Version 1.8:
- Introduced \labelgraphics to auto-display image filename below the image.

Version 1.7.1:
- Changed interlude slide labels to: "Slide Interlude".

Version 1.7:
- Added auto-detection of the number of pages in PDFs.

Version 1.6:
- Grouped user-specified variables.
- Cleaned up code and eliminated redundant elements.

Version 1.5:
- Converted \begin{slideannotate} command to slideannotate environment.

End of README.