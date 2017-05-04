+++
date = "2017-05-03T20:40:26-06:00"
title = "Hugo v0.20 Content Organization Warning"

+++

Content Organization in Hugo v0.20
===

Recently the [Hugo](https://gohugo.io) team introduced version 0.20 which included brand new [Custom Output Formats](http://gohugo.io/extras/output-formats/).
However, before you dive in to play with these new tools, be aware that the release did cause problems for some users. In certain cases, some files ended up in unexpected locations when a site was published.

These problems were related to [Content Organization](http://gohugo.io/content/organization/). The most common method for organizing files is to maintain separation between content files and static files. For example, a content file which is to be processed by Hugo might be stored as `content/blog/post1.md` and an associated image might be stored as `static/images/blog/image1.jpg`. Following this pattern continues to work with no unexpected issues.

However, some users prefer an alternative method of content organization which groups all files relating to a single post together in one folder. In this case, we could expect to see a folder like `content/blog/post1/` and inside that folder would be both `index.md` and `image1.jpg`. It was cases such as this which ran into unexpected site changes with v0.20.

When publishing a post, users would expect their new content to be found at `public/blog/post1/index.html`. Instead, the index.html page was bumped down another level, which resulted in `public/blog/post1/index/index.html`. To see the reason behind this, take a look at what Hugo calls ['pretty URLs'](https://gohugo.io/extras/urls/). Hugo considers something such as `public/blog/post1/index.html` to be a 'pretty URL' because it is accessible in the browser as `https://example.com/blog/post1/`. Alternatively, `https://example.com/blog/post1.html` is considered an 'ugly URL'.

So, in an attempt to 'prettify' URLs, Hugo v0.20 could result in paths such as `https://example.com/blog/post1/index/index.html`. Fortunately, there were a flurry of updates following v0.20 and a workaround for this particular issue was added in v0.20.6. Essentially, some file names are exempted from the pretty URL process, which will then produce the expected output. `index.md` is treated as an 'ugly URL' and is output as `index.html` instead of `index/index.html`. Take a look at the [pull request](https://github.com/spf13/hugo/pull/3401) for more details or to view the code changes.

Finally, note that [Forestry.io](https://forestry.io) currently uses v0.20.2 as the latest available version. If you wish to use this Hugo version, but believe that you may be affected by the issue noted above, there is a potential workaround to try. You are able to define the [slug](http://gohugo.io/content/organization/#slug) in the Front Matter. By doing so, Hugo does not generate the destination using the filename, but rather the slug. In this case, try setting `slug = ‘/‘` to see if this resolves the issue described above while using v0.20.2.
