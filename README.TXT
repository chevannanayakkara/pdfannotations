README FOR pdfannotations PACKAGE
=================================

Version: 3.1
Date: 2023-11-22

Overview
--------
pdfannotations is a LaTeX package designed for annotating PDF slides with LaTeX elements, adding interludes, and including code snippets. In its latest version, the package has been enhanced with improved error handling and debug logging for more robust and informative user interaction. It offers a flexible way to enhance PDF presentation slides with additional LaTeX content. The package utilizes LaTeX3 syntax and requires the pdfLaTeX compiler.

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

Here are the descriptions for each part of the user configuration section of your script:

- `\newcommand{\MyTitle}{...}`: This command defines the title of your document. 

- `\newcommand{\MyAuthor}{...}`: This command sets the author's name for the document. 

- `\newcommand{\MyDate}{...}`: This command defines the date associated with the document. 

- `\newcommand{\FirstSectionName}{...}`: This command sets the name of the first section or chapter in your document. 

- `\newcommand{\PDFMaxWidth}{0.80\textwidth}`: This command specifies the maximum width for included PDF pages as a percentage of the text width of the document. Here, it's set to 80% of the text width. This ensures that included PDFs are scaled appropriately to fit within this width.

- `\newcommand{\MaxInterludes}{20}`: This command sets the maximum number of interludes (breaks or separate sections) allowed in the document. The value `20` can be adjusted based on the number of interludes you plan to include.

- `\newcommand{\PDFList}{"Career.pdf"}`: This command creates a list of PDF files to be used in the document. It's currently set to include only one file, "Career.pdf." This list can be modified to include multiple PDFs by separating the filenames with commas within the curly braces.

These commands provide a customizable framework for your document, allowing you to easily adjust key elements like the title, author, date, and specific document settings.

System Requirements
-------------------
- LaTeX3 syntax.
- pdfLaTeX compiler.

Successfully Tested With Packages
---------------------------------
{mathtools} - Enhances the presentation and formatting of mathematical content in documents. Provides various tools and utilities that extend the capabilities of amsmath.

{cancel} - Allows for the placement of simple cancellation lines through parts of mathematics formulas. Useful for demonstrating the process of simplifying expressions.

{booktabs} - Provides additional commands to enhance the quality of tables in LaTeX documents. Known for enabling the creation of more professional-looking tables without vertical separators.

{array} - Extends the options for column formats within tables, offering greater flexibility and control over the layout and presentation of table content.

{longtable} - Facilitates the creation of tables that continue over multiple pages. This package is essential for handling large tables that do not fit on a single page.

{mathrsfs} - Offers access to the mathematical script font for use in LaTeX documents. Ideal for typesetting script-style mathematical expressions.

{mathtools} (listed twice, so the same description applies) - Enhances the presentation and formatting of mathematical content in documents.

{scrlayer-scrpage} - Provides user-friendly interfaces for creating and managing headers and footers in documents. It's a component of the KOMA-Script bundle.

{xcolor} - Allows for easy driver-independent use of color in LaTeX documents. It supports various color models and offers a range of utilities for color manipulation.

{listings} - Used for formatting source code listings with syntax highlighting. Supports a wide range of programming languages and offers customization options.

{seqsplit} - Useful for splitting long sequences of characters, typically in situations where long strings need to be broken down to fit into the layout without overflowing the margins.

{enumitem} - Provides control over the layout of itemize, enumerate, and description environments. It allows for easy customization of labels and spacing in lists.

{adjustbox} - Offers an environment and macros to adjust general content (boxes). Particularly useful for scaling, resizing, trimming, or constraining content dimensions such as images or tables.

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

Version 3.1 (2023-11-22):
- Introduced `PDFMaxWidth` for dynamic scaling of included PDF documents.

Version 3.0 (2023-11-21):
- Improved error trapping and messages for empty or malformed PDF List.
- Provided verbose messages in the document for out of bounds indexes for \annotatepdf and \listpdfs
- Added detailed debug log information, search for "PDFAnnotations"


Version 2.4.1 (2023-11-15):
- Added new command \listpdfs that shows all PDFs and their index number for use with the \annotatepdf command.

Version 2.3 (2023-11-10):
- Brought all user-specified variables to the top of the preamble for easier customization.
- Added \listpdfs command to list all PDFs and their index numbers.

Version 2.2.3 (2023-11-08):
- Added packages booktabs and longtable for table environment support.
- Reformatted the entire document for improved readability and structure.

Version 2.2.2 (2023-11-07):
- Removed the changelog from the code to be included in the README file instead.

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
