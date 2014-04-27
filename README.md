Hyde for Hugo
=============
>A port of [Hyde][hyde] for the [Hugo][hugo] static site generator

[hyde]: https://github.com/poole/hyde
[hugo]: https://github.com/spf13/hugo

Getting started
---------------
Get Hugo from [here][get-hugo] and put it somewhere in your `$PATH` (`~/bin`
works well, just make sure your `.bashrc` / `.zshrc` / `config.fish` is adding
it).

[get-hugo]: https://github.com/spf13/hugo/releases

```bash
# Clone the repo
git clone git@github.com:ciarand/hyde-for-hugo.git
cd hyde-for-hugo
# begin serving files
hugo serve -w
```

Start messing with it! Your content files will be recompiled with your layout
files any time either of them change.

Current status
--------------
Done! Up to date (as much as it can be) with the original [Hyde][hyde].

Missing features
----------------
Hugo doesn't support pagination right now. It's on their roadmap, and when they
add it I'll do the same.

License
-------
[@mdo][mdo] generously distributes Hyde under the MIT license. Since this is a
100% derivative work I'm going to stick with that. If you've never seen the MIT
license, you can see it [here][license].

[mdo]: https://github.com/mdo
[hugo-license]: https://github.com/spf13/hugo/blob/master/LICENSE.md
[license]: /LICENSE.md

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
