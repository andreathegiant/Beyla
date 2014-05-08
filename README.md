Beyla
=====
A [Middleman](http://middlemanapp.com/) prototyping tool with [Alphecca](https://github.com/opensourcery/alphecca)-flavored markup, and [Foundation's](foundation.zurb.com) grid system. This tool allows you to prototype using Alphecca stylings, so that when you're developing an unthemed Drupal site, and you use the Alphecca theme, it will look just like the prototype! Huzzah!

## Dependencies
You will need to install the Middleman Ruby gem:
`gem install middleman`

You also need Compass:
`gem install compass`

And Sass:
`gem install sass`

### Optional: using Bundler to manage dependencies
Running Middleman through [Bundler](http://bundler.io) can help resolve Ruby dependencies (See *Troubleshooting* below). To install Bundler:

`gem install bundler`

## Installing Beyla
Clone the git repository.

`git clone git@github.com:andreathegiant/Beyla.git`

You can then `cp` this directory (minus its `.git` subdirectory) into your new project. For a [turnip project](http://github.com/opensourcery/turnip), typically this becomes a `wires` directory that lives at the root of turnip.

To run a static HTML build of the prototype, which ensures that middleman is building properly, in the `wires` directory run `middleman build` and view the `build/index.html` file. This page should have a slider, three block regions, a footer, a main nav and and quicklinks.

## Working with Beyla

If you open a new terminal tab and in the `wires` directory run `middleman server` you can navigate to `localhost:4567` in your browser to see a live reloaded version of the prototype as you're working.

The only folder you should need to work with when prototyping is the `source` directory. In this directory you will find a number of different files types.

## Troubleshooting

If you receive an `Gem::LoadError` like this:

```
You have already activated middleman-core 3.3.2, but your Gemfile requires middleman-core 3.2.2. Prepending `bundle exec` to your command may solve this. (Gem::LoadError)
```
… you can either run middleman through Bundler (see *Optional: Using Bundler to manage dependencies*), or you can resolve the dependencies by editing your `Gemfile` and/or updating your gems manually.

### Partials
`_[name].erb` Files with this file extension are partials, which are small snippits of HTML or ruby that can be included in page or in template files. Good uses for partials are menus, blocks, footers, slideshows. To include a partial in a page or template, all you write is `<%= partial "path/to/partial" %>`. Do not append .erb at the end of the partial name.

## Pages
`[name].html.erb` Files with this extension are pages, which are to be generated in static HTML when the `middleman build` is run. Good uses for pages are individual pieces of content, such as a blog post or an individual user profile.

## Layouts
* In `source/layout` you will find `[name].erb` files (note the lack of underscore in the front) which define the layouts for pages. To give a page a specific layout, at the top of the `.html.erb` file, as follows:
```
---
layout: blog
---
```

Beyla uses the [Foundation 4 grid system](http://foundation.zurb.com/docs/v/4.3.2/components/grid.html). Most of the layout should be determined in the layout file, however on occasion it is necessary to define layouts within a page or a partial.

##Linking in your files
There are two template helpers in Middleman for linking. First, there is the middleman equivalent to an `<a>` tag, `erb <%= link_to 'Link Title', 'path/to/page.html' %>`. Additionally, there is the the link block template helper, which is for complex objects that should be linked in full, like an image or entire block:

```erb
<% link_to 'Link Title', 'path/to/page.html' do %>
   <%= image_tag 'mylogo.png' %>
<% end %>
```

It is very important to use `link_to` because of Middleman's relative linking functionality. Without this, your links will link to the wrong place on build in a subdirectory, e.g.  if the root of your prototype lives at `http://example.com/mysite

Similarly, it is important in your layout files to use the `<%= stylesheet_link_tag 'path/to/stylesheet %>` helper. Do not include .css at the end, additionally, this template helper looks only in the `stylesheet` directory within `source`, so do not place relevant files outside of this directory.

In the same vein, it is important for your layout files ot use the `<%= javascript_link_tag 'path/to/js' %>` helper. This template helper looks only in the `javascripts` directory within `source`, so do not place relevant files outside of this directory.

## Cool Things
* Beyla is using [Chosen](http://harvesthq.github.io/chosen/), a select list UI improver. A working example of this in Beyla can be found on the [About](https://github.com/andreathegiant/Beyla/blob/master/source/about/about.html.erb) page.
* Any of the Foundation Javascripty goodness can be used in Beyla.
* Middleman comes with a lorem ipsum and placeholder image generator. These are being used to generate images in the [homepage slider](https://github.com/andreathegiant/Beyla/blob/master/source/_orbit.erb), and placeholder content for the [blocks on the homepage](https://github.com/andreathegiant/Beyla/blob/master/source/_homepageblocks.erb).

## Further reading
* [Middleman documentation](http://middlemanapp.com/basics/getting-started/)
* [Foundation 4 documentation](http://foundation.zurb.com/docs/v/4.3.2/)
* [Alphecca documentation](https://github.com/opensourcery/alphecca/blob/master/README.md)
