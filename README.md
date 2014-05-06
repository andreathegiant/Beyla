Beyla
=====
A work in progress to make a Middleman prototyping tool with Alphecca markup.

## Dependencies
You will need to install the Middleman Ruby gem:
`gem install middleman`

You also need Compass:
`gem install compass`

And Sass:
`gem install sass`

## Installing Beyla
Clone the git repository.

`git clone git@github.com:andreathegiant/Beyla.git`

You can then `cp` this directory (minus its `.git` subdirectory) into your new project. For a [turnip project](http://github.com/opensourcery/turnip), typically this becomes a `wires` directory that lives at the root of turnip.

To run a static HTML build of the prototype, which ensures that middleman is building properly, in the `wires` directory run `middleman build` and view the `build/index.html` file. This page should have a slider, three block regions, a footer, a main nav and and quicklinks.

## Working with Beyla

If you open a new terminal tab and in the `wires` directory run `middleman server` you can navigate to `localhost:4567` in your browser to see a live reloaded version of the prototype as you're working.

The only folder you should need to work with when prototyping is the `source` directory. In this directory you will find a number of different files types:

* `_[name].erb` - these are partials, that can be included in a page or in a template.
* `[name].html.erb` - these are pages to be generated in HTML when the static site is built.
* In `source/layout` you will find `[name].erb` which define the layouts for an `html.erb` pages. To give a page a specific layout, at the top of the `.html.erb` file, as follows:
```
---
layout: blog
---
```

Beyla uses the [Foundation 4 grid system](http://foundation.zurb.com/docs/v/4.3.2/components/grid.html).

You can use Ruby to include partials, and perform other basic functions, such as looping or block linking.
