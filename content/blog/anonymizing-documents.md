+++
title = "Anonymizing Documents and Images"
date = 2025-02-03
description = "A non-exhaustive summary of how to anonymize documents and images."
authors = ["Andrew Dunham"]

[taxonomies]
categories = ["Tech"]
tags = ["privacy", "tech"]

[extra]
lang = "en"
toc = true
+++

This blog post is a non-exhaustive summary of how to anonymize documents and
images. It is intended to be a quick reference guide for those who need to
share documents or images with others while protecting the privacy of the
individuals involved.

<!-- more -->

## Introduction

This is a high-level summary of some techniques that can be used to fingerprint
(sometimes called "watermark") documents and images. It is not a comprehensive
guide, and it is not a guarantee of privacy.

{% warning() %}
Do **not** rely on this post to be a comprehensive guide, especially against
extremely well-resourced actors. This is a quick reference guide and a starting
point, not a tutorial.
{% end %}

## Fingerprinting, Watermarking, and Document Identification

Broadly speaking, there are a few categories of techniques that are used to
allow identifying the origin of a document or image:

1. Metadata in the file itself, such as the author or creation date embedded in
   a Word document.
2. Watermarks or other embedded information in the file, such as a watermark in
   an image (hidden or otherwise), white-on-white text, etc.
3. Sending different versions of the document to different recipients, so that
   the recipient can be identified by the version they receive.

Each of these techniques has its own strengths and weaknesses, and they need
different mitigations to defeat. Documents may use one, two or even all of
these techniques together, so it's important to be aware of all of them.

## Document Anonymization

### Metadata

Metadata is information that is stored in the file itself, such as the author,
creation date, and other information. This information can be used to identify
the author of a document, the software used to create it, and other
information.

A common case of metadata is in images, where the camera model, exposure time,
and GPS location is embedded in the image file itself. This can be used to
identify the camera that took the photo, and potentially the location where it
was taken. Some privacy-focused applications will strip this metadata; for
example, Signal removes the location (and most other metadata) from images, so
sending a photo to yourself in Signal is an easy way to ensure that basic
metadata is removed.

A more reliable way to defeat document metadata is to transform the document
into a different format that does not support metadata. For example, if you're
trying to anonymize a Word document, printing it out and then scanning it
again, or taking a photo of the document on a screen, will remove all the
metadata.

{% tip() %}
If you're taking a photo of a screen, make sure to strip the metadata from the
photo itself! And make sure that there's no reflections in the monitor that
could reveal who took the photo.
{% end %}

Note that this does *not* always work if you simply convert one image format to
another, or one document format to another. For example, converting a Word
document to a PDF may not remove the metadata.

### Watermarks

Watermarks are information that is embedded in the document itself. You've
probably seen this in images, where a faint "COPY" is printed across an image,
or where stock photos have semi-transparent text over top of them so they
cannot be used without paying for a license.

This can be done in a variety of ways, from the visible (as mentioned above) to
more invisible techniques. For example, some printers will print a pattern of
yellow dots on the page that can be used to identify the printer that printed
the document; see [Wikipedia][printer-dots] for more information on this
particular technique.

[printer-dots]: https://en.wikipedia.org/wiki/Printer_tracking_dots

In general, the best way to defeat watermarks is to transform the document
"manually" - if it's a text document, re-type it by hand; if it's an image,
redraw it by hand. This is not always practical, but it is the most effective
way to defeat watermarks.

There are some techniques that can help here but aren't guaranteed to work;
stuff like rendering an image in black and white can defeat invisible or
low-contrast watermarks, for example, but this doesn't always work and there
are known ways to bypass this.

### Different Versions

One of the most effective ways to identify the recipient of a document is to
send different versions of the document to different recipients. This can be
done in a variety of ways, such as changing the text slightly, changing the
spacing between words, the font, and an infinite number of other small
modifications.

This also doesn't need to be done per-recipient; you can send a different
version to several groups of recipients, and then see which version is made
available. Then, you can repeat that process with the recipients who received
that version, and so on until an individual recipient is identified.

Defeating this technique is difficult, and is best done by obtaining multiple
copies of the same document from multiple sources, removing all the metadata
and watermarks as mentioned above (ideally, by re-typing text documents
entirely to remove formatting and spacing differences), and then comparing the
documents to see if there are any differences.

## Resources

### Further Reading

- [Data and Metadata Redaction](https://www.privacyguides.org/en/data-redaction/), from Privacy Guides
- _more to come_

### Tools

- [ExifTool](https://exiftool.org/) - A tool for reading and writing metadata in
  images and documents.
