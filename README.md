Intro
=====

**richly** converts markdown or emacs org-mode files into html and
renders latex as inline svg. You can visit
[this page](https://xwcal.github.io/posts/2024/07/10/self_closing_loop_generators/) or
[this page](https://xwcal.github.io/posts/2024/02/29/jane-st-202303-robot-long-jump-solution/)
to see its product.

The initial iteration I wrote overnight a few years ago also included
PlantUML integration (thus the name \"richly\"). The diagramming feature
can be added back if there is popular demand.

Dependencies
============

In order to use richly, you need:

-   a working latex setup that generates dvi output
-   pandoc
-   dvisvgm
-   python3
-   linux

Basic usage
===========

The `<input file>` below should be either a `.md` or a `.org` file.

For a one shot conversion:

    $ richly <input file> <output file>

To let richly monitor `<input file>` and do incremental conversion as
you edit it, add the -s switch:

    $ richly -s <input file> <output file>

In either case, you may find the `-v` switch helpful.

Hugo integration
================

If you use org-mode, the input org files can coexist with markdown files
under `content/`: simply add `"\\.org$"` to `ignoreFiles` in your site
configuration file.

Say you are writing a post named `some-post.org`, you need to enclose
the front matter between `#+begin_src` and `#+end_src`, then run
`richly` with the `-r` switch:

    $ richly -s -r -v some-post.org some-post.md

With `hugo server` running you can see the result update in real time as
you edit `some-post.org`.

If you use markdown, you need to keep a seperate \"richly source files\"
directory outside your hugo site directory so that hugo doesn\'t get
confused. And you need to enclose the front matter in a code block using
a pair of ```` ``` ```` (or more backticks if necessary) instead.

TODOs
=====

Add an option for saving and restoring the cache to avoid potentially
lengthy cold starts.
