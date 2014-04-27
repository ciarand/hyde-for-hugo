---
title: Differences between Hugo and Jekyll
slug: differences-between-hugo-and-jekyll
date: 2014-04-26
type: post
---

Theming in [Hugo][] presents a unique set of challenges to both the experienced
and novice Jekyll themer. Hugo's templates aren't built with native support for
nested contexts (layouts) like Jekyll's, so the enterprising themer needs to
create those facilities themselves. Luckily, using a series of conventions
not dissimilar to Jekyll's makes the process fairly painless.

[Hugo]: http://hugo.spf13.com/

Let's examine some of the hacks that this theme uses.

Layouts
-------
Since Hugo's natural behavior doesn't include any facilities for true extendable
layouts the naive approach is to store common HTML elements like the `<head>`
and the doctype in "partials." Unfortunately, this has several downsides:

- Editor support for HTML elements without closing tags is lacking

- It forces each layout file to include the same partials in the same order in
  order to maintain a consistent appearance

Instead, this is the approach I've taken:

- Use the `layouts/_defaults/single.html" as the entry point for every page and
  post in the theme. This means we have one unified layout that guarantees an
  identical starting structure for every page.

- Set a new default layout file that's used instead of the `section/single.html`
  file (in this case it's a `section/layout.html` file).

- Use custom section types for the home and archive pages.

Indexes
-------
Support for indexes in Hugo is… interesting. The `.Site.Indexes` map doesn't have
knowledge of the section-specific indexes - only the user defined indexes like
"tags" and "categories." Since I'd rather not force any taxonomical organization
on the user I've opted to instead use a new content type, "index," that uses a
custom parameter ("data") to store the content type to index.

So, section-specific indexes have front matter that looks like this:

{{% highlight php %}}
title:  "Archive"  # the title of the page
url:    "/archive" # the URL of the page
type:   "index"    # (req'd) marks this as an index
data:   "post"     # (req'd) the type to index.
{{% /highlight %}}

How do I create a new content type?
-----------------------------------
Easy. Let's say we're creating a `quote` content type. Create a new .md file in
`content`. Let's call it `famous-quote.md`. Add the following content:

<!-- Using PHP b/c there's not a Pygments filter for markdown + yaml -->
{{% highlight php %}}
---
# this is the important one
type: quote

# standard frontmatter
title: Famous Quote
slug:  famous-quote
date:  2014-04-26

# We can also include custom attributes in any content
# these will be accessible under .Params.paramname
# Check http://hugo.spf13.com/layout/variables for more info
source: George Washington
---
Be courteous to all, but intimate with few, and let those few be well tried before you give them your confidence.
{{% /highlight %}}

Now, obviously we want quotes to be displayed differently from a standard post.
Let's create a custom template. Create a new folder in `layouts` for your
`quote` layout. Then add the `layouts/quote/layout.html` file. It will probably
look something like this:

{{% highlight html %}}
<blockquote>
    {&#123; .Content }}

    {&#123; if .Params.source }}
        <cite>{&#123; .Params.source }}</cite>
    {&#123; end }}
</blockquote>
{{% /highlight %}}

That's it! Our inspiring new quote should be displaying (at the slug we
specified earlier) in our new template. Easy!
