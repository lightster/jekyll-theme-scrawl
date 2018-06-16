# The Scrawl theme

**Organize documentation, playbooks, and other composition with Scrawl**

Scrawl is a page-centric theme for Jekyll.  Rather than catering to posts like most Jekyll themes, Scrawl focuses on providing categorization and navigation for pages.

*The Scrawl theme is based on GitHub's [Primer theme](https://github.com/pages-themes/primer) and the left navigation is inspired by Steve Smith's [Minimal](https://github.com/orderedlist/minimal).*

## Installation

Set Jekyll's `_config.yml` to pull the theme from the `lightster/jekyll-theme-scrawl` remote theme:

```yaml
remote_theme: lightster/jekyll-theme-scrawl
```

## Usage

Scrawl is all about pages.

### Pages and their URLs

You will most likely want to create an `index.md` in the root of your Jekyll site.  This is the page that the browser will load when first arriving at your site.

You can create more pages in the root of your Jekyll site, as well as subdirectories of the Jekyll site.  Page URLs match the paths that appear in your site directory structure.

We like our page URLs to leave off the `.html`, so we include the following in our `_config.yml`:
```yaml
permalink: pretty
```

### Layouts

Scrawl provides the following layouts:

 - `base` — The `base` layout is the base layout used by all other layouts.  The base layout has two side-by-side independently scrolling panes.  The left pane contains the site title, the site description, and the navigation.  The right pane is wider and is used for displaying the content.
 - `page` — The `page` layout is the default layout that pages use.  The page layout is similar to the base layout but with a few additions:
   - The `title` value provided in the page's front matter is displayed as a header above the page content
   - The calculated estimated reading time.  This can be disabled by setting `reading_time` to `false` in the page front matter.
   - The `summary` value provided in the page's front matter is displayed below the page title and reading time
   - A table of contents is displayed below the page title and summary.  The table of contents is generated based on the page's level 2, 3, and 4 headers (`<h2>`, `<h3>`, and `<h4>` tags). This can be disabled by setting `toc` to `false` in the page front matter.
 - `sitemap` — The `sitemap` layout breaks the navigation into four columns that takes up the width of the layout.

You can set the layout for a page in the page's Jekyll front matter:
```yaml
---
layout: base
---
```

#### Widths

For the `default` and `page` layouts, there is a `width` setting for controlling how wide the content pane should be:
 - `fixed` — The `fixed` width is the default.  The fixed width layout stays the same width unless the browser window is not wide enough, in which case the navigation is moved into a hamburger menu and the page takes up the width of the browser window.
 - `fluid` - The `fluid` width takes up the width of the browser window.  If the browser window is not wide enough, the navigation is moved into a hamburger menu.
 - `no-nav` – The `no-nav` width behaves like the `fixed` width setting, but it removes the navigation, allowing the content pane to take up the entirety of the fixed width.

You can set the width for a page in the page's Jekyll front matter:
```yaml
---
width: fluid
---
```

#### Mobile-friendly

All layouts and widths are mobile-friendly.

### Navigation

The navigation is generated by aggregating all pages' front matter.  By default, a page is included in the navigation as long as the page has a non-empty `title` value in its front matter.

#### Ordering links

Pages are sorted in the navigation based on the `order` value that you provide in the page front matter.  You can set the `order` value to the same value as the page's title to order the pages in the navigation alphabetically.

If you do not set an `order` value, the ordering of items in the navigation is undefined and may vary between site builds.

#### Changing the link text

The `title` that appears in the front matter of the page is used for link text.  If you want the link text to be something other than the page title, such as an abbreviated version of the page title, you can set `nav_title` in your page front matter.

#### Hiding links

If you have a page with a title but you do not want the page to appear in the navigation, you can exclude the page by setting `hide_in_nav` to `true` in your page front matter.

### Page Categories

Scrawl allows pages to be organized into categories.  These categories are used when displaying the pages in the side navigation and the site map.

Note that categories do not affect a page's URL.  As noted in [Pages and their URLs](#pages-and-their-urls), page URLs match the paths that appear in your site directory structure.

#### Declaring categories

Before pages can be placed in categories, you need to define the categories.  Categories are defined by creating a `_data/scrawl.yml` file and listing categories like so:
```yaml
categories:
  - title: Lunch
    order: 1
    key: lunch
  - title: Dinner
    order: 2
    key: dinner
  - title: Beverages
    order: 3
    key: beverage
```

Each category should contain all three keys:
 - `title` — The title appears in the navigation and site map as the title of the category.
 - `order` — The order determines the order the category should appear relative to the other categories.
 - `key` — The key is the value that is used in page front matter to place the page in the category.

#### Placing a page in a category

Once the categories are defined, you can place a page in a category by setting the `category` value in the page front matter like so:
```yaml
---
category: beverage
---
```

### Custom CSS and JavaScript

If you need to add custom CSS or JavaScript tags, you can create `_includes/head.html` and/or `_includes/foot.html` files containing the `<link>` and/or `<script>` tags you need added to your pages.

For custom CSS, you will generally want to place `<link>` tags in `_includes/head.html`.

For custom JavaScript, you will want to place your `<script>` tags in `_includes/head.html` if you are using the `defer` attribute or otherwise need the `<script>` tag to appear in the page's `<head>` tags.  If you are not using `defer` and do not need the JavaScript to load in the `<head>` tag, you should place your `<script>` tags in `_includes/foot.html` so they will be added just above the page's closing `</body>` tag.

## Development

To set up your environment to develop this theme, fork this repo, clone your fork to your localhost, and run `bundle install`.

The theme is setup just like a normal Jekyll site. Run `bundle exec jekyll serve` and open your browser to [`http://localhost:4000`](http://localhost:4000). As you make changes to your clone of the theme, your site will regenerate and you should see the changes in the browser after a refresh, just like normal.

When the theme is released, only the files in `_layouts`, `_includes`, `_sass` and `assets` tracked with Git are bundled.

## License

The theme is available as open source under the terms of the [MIT License](LICENSE).
