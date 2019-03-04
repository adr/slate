# The ADR Slate Theme [![Build Status](https://travis-ci.org/adr/slate.svg?branch=master)](https://travis-ci.org/adr/slate)

> ADR Slate is a Jekyll theme for GitHub Pages. It is a modified version of [Slate](http://pages-themes.github.io/slate).
> It adds support for [AnchorJS](https://www.bryanbraun.com/anchorjs/) and [sticky headers](https://www.w3schools.com/howto/howto_js_sticky_header.asp)

![Thumbnail of Slate](thumbnail.png)

## Usage

To use the ADR Slate theme:

Add the following to your site's `_config.yml`:

```yml
theme: adr/slate
```

## Customizing

### Configuration variables

Slate will respect the following variables, if set in your site's `_config.yml`:

```yml
title: [The title of your site]
description: [A short description of your site's purpose]
```

Additionally, you may choose to set the following optional variables:

```yml
show_downloads: ["true" or "false" to indicate whether to provide a download URL]
google_analytics: [Your Google Analytics tracking ID]
anchors: ["true" or "false" to load anchor.js form cdnjs.cloudflare.com]
```

### Stylesheet

If you'd like to add your own custom styles:

1. Create a file called `/assets/css/style.scss` in your site
2. Add the following content to the top of the file, exactly as shown:

    ```scss
    ---
    ---

    @import "{{ site.theme }}";
    ```

3. Add any custom CSS (or Sass, including imports) you'd like immediately after the `@import` line

*Note: If you'd like to change the theme's Sass variables, you must set new values before the `@import` line in your stylesheet.*

### Layouts

If you'd like to change the theme's HTML layout:

1. [Copy the original template](https://github.com/adr/slate/blob/master/_layouts/default.html) from the theme's repository  
   (*Pro-tip: click "raw" to make copying easier*)
2. Create a file called `/_layouts/default.html` in your site
3. Paste the default layout content copied in the first step
4. Customize the layout as you'd like

### Overriding GitHub-generated URLs

Templates often rely on URLs supplied by GitHub such as links to your repository or links to download your project. If you'd like to override one or more default URLs:

1. Look at [the template source](https://github.com/pages-themes/slate/blob/master/_layouts/default.html) to determine the name of the variable. It will be in the form of `{{ site.github.zip_url }}`.
2. Specify the URL that you'd like the template to use in your site's `_config.yml`. For example, if the variable was `site.github.url`, you'd add the following:

    ```yml
    github:
      zip_url: http://example.com/download.zip
      another_url: another value
    ```

3. When your site is built, Jekyll will use the URL you specified, rather than the default one provided by GitHub.

*Note: You must remove the `site.` prefix, and each variable name (after the `github.`) should be indent with two space below `github:`.*

For more information, see [the Jekyll variables documentation](https://jekyllrb.com/docs/variables/).

### Previewing the theme locally

If you'd like to preview the theme locally (for example, in the process of proposing a change):

1. Clone down the theme's repository (`git clone https://github.com/adr/slate`)
2. `cd` into the theme's directory
3. Run `script/bootstrap` to install the necessary dependencies
4. Run `bundle exec jekyll serve` to start the preview server
5. Visit [`localhost:4000`](http://localhost:4000) in your browser to preview the theme

### Running tests

The theme contains a minimal test suite, to ensure a site with the theme would build successfully. To run the tests, simply run `script/cibuild`. You'll need to run `script/bootstrap` one before the test script will work.
