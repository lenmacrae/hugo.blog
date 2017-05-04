+++
date = "2017-05-03T20:41:52-06:00"
title = "Hugo Custom Output Formats"

+++

Hugo Custom Output Formats
===

Hugo v0.20 introduced a powerful new feature for your sites -- [Custom Output Formats](http://gohugo.io/extras/output-formats/). As the release notes proudly proclaim:

> Hugo isn’t just that “static HTML with an added RSS feed” anymore. Say hello to calendars, e-book formats, Google AMP, and JSON search indexes, to name a few.

Do you want to produce a page in multiple formats? Do you want to present content as CSV, AMP, or a calendar? Do you want to work with something more specialized? No problem! You can now do all this and more with Hugo's Custom Output Formats.

There are two main components when producing a Custom Output Format, a media type and an output format. Hugo v0.20 now includes the following set of built-in media types: `javascript, json, rss, xml, calendar, css, csv, html, plaintext`. These can be output in one or more of these built-in formats: `AMP, CSS, CSV, Calendar, HTML, JSON, RSS`. Immediately you can see the new possibilities that this feature enables for your sites.

But, these new built-ins are only the tip of the iceberg. The real excitement is in the fact that these are *Custom* Output Formats. You can easily create a new format or modify one of the existing defaults. The first step is to edit the site config so that there is a `mediaTypes` section. Each media type needs a type identifier and a file suffix. Once a media type is defined, you can proceed to define the `outputFormats`. Each media type can be output in multiple different formats, so long as each one has a unique file path. For example, you can output HTML as `/index.html` and AMP as `amp/index.html`.

The final step is to make sure there is a proper template setup for each new output format that you are using. Take a look at the [documentation](http://gohugo.io/extras/output-formats/) and get started making your Hugo sites even better than they are today!
