Hyde for Hugo
=============
>A port of [Hyde][hyde] for the [Hugo][hugo] static site generator

[hyde]: https://github.com/poole/hyde
[hugo]: https://github.com/spf13/hugo

Current status
--------------
In progress. I've ripped out most of the Ruby stuff and most of it is a pretty
simple transition. Stuff like `{% highlight js %}` becomes `{{% highlight js
%}}`, `site.title` becomes `.Site.Title`, `for`s become `range`s, etc.

The site mostly looks ok, but the code needs some fixing up in places. The
layouts especially need some love, as there's an uncomfortable amount of code
repetition throughout.

Versioning
----------
Let's say I'm following [semver][] until 1.0, at which point I'll bump the
version number to match [upstream][hyde].

[semver]: http://semver.org/

Roadmap / commentary
--------------------
The layout engine in Hugo is not as intuitive as Jekyll's. Right now each
template needs to include the `chrome/header` and `chrome/footer`, which reminds
me of PHP in the early 2000s. We can do better.

RSS is currently broken, and I need to look into why. It's not a high priority
for me though.

Filenames can be rewritten, and a better comparison of why you'd pick this over
Jekyll also needs to be written.

Finally I'd like to refactor some of the code I'm inevitably going to write for
this out into a Hugo starter package. Something that offers a prebuilt directory
structure that's not as intimidating as the Hugo docs. Something to think about.

Missing features
----------------
Hugo doesn't support pagination right now. It's on their roadmap, and when they
add it I'll do the same.

License
=======
Hugo uses the ([slightly unusual][hugo-license]) "Simple Public License" which
claims to be "a plain language implementation of GPL 2.0." However, since I'm
not distributing Hugo (or even Go, just a set of templates that are compatible
with Go's standards) and this isn't based on any of the Hugo code I don't think
that applies.

On the other hand, [@mdo][mdo] distributes Hyde under the MIT license. Since
this is a 100% derivative work I'm going to stick with that. If you've never
seen the MIT license, you can see it [here][license].

[mdo]: https://github.com/mdo
[hugo-license]: https://github.com/spf13/hugo/blob/master/LICENSE.md
[license]: /LICENSE

Glossary
--------
[Jekyll][jekyll] is a Ruby generator for static sites. That means it transforms
a folder full of Markdown files and some HTML templates into a bunch of HTML
that can be deployed pretty much any where, including gh-pages, Dropbox, your
grandma's shared hosting account, etc.

[Hyde][hyde] is an awesome theme for Jekyll, created by the talented
[@mdo][mdo]. It's clean, responsive, and has a whole bunch of goodies built-in.
Check it out.

[Go][go] is a compiled language that aims to be fast and efficient. It was
created by some very smart people at Google.

[Hugo][hugo] is to Go as Jekyll is to Ruby, and I like Go more than I like Ruby.

[jekyll]: http://jekyllrb.com/
[go]: http://golang.org/
