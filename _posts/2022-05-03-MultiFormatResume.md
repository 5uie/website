---
layout: post
title:  "Creating a resume in multiple formats"
date: 2022-05-01 17:48:00 +0530
tags: resume pandoc latex 
blurb: Using a pandoc based system to generate a resume in multpiple formats like html, pdf and docx 
---

Maintaining and updating a resume is often an uphill task. In modern times, due to the demand and needs from different resume processing systems, multiple formats are often needed. 

Over the course of two decades, I have only changed the format of my resume twice. It makes sense to create a template for multiple formats and then keep updating the text to generate the files in different formats. 

In my use case, I have a need for publications to show up and to have a logo of the organisation I am representing in some cases. Additionally, I need to share the resume in PDF and DOCX based on the uses. While it might be possible for some users to convert/print/export a DOCX file as a PDF, this workflow is not possible for users without access to good word processing software. LaTeX<label>[1](),[2]()</label> handles typesetting much better and supplies greater flexibility for customisation and therefore I chose this way. I did realise that having a web presence is important for folks now, therefore have added a HTML format too. 

A [pandoc](https://pandoc.org/) based workflow seemed to work best for me. 

## Workflow

1. Resume in markdown format
2. Style files for HTML, LaTeX and DOCX
3. References in a separate bib file
4. Any added material (images, logos, etc.)
5. Use pandoc to generate necessary outputs

## Source

The project is available on [Github](https://github.com/5uie/mfr_pandoc), please do feel free to use it and in case you have questions, you can always reach out.


[1](https://towardsdatascience.com/why-should-you-learn-latex-or-at-least-give-it-a-try-8d0f3218b8e?gi=5bb8209352c9)
[2](https://nitens.org/w/latex/)
