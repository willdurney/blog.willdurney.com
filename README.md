# blog.willdurney.com

Source for [Prattle of Will's](https://blog.willdurney.com) — a personal blog about tech, pop culture, and the world. Built with [Jekyll](https://jekyllrb.com/) and the [Hydeout](https://github.com/fongandrew/hydeout) theme.

## Prerequisites

- [Ruby](https://www.ruby-lang.org/) (2.5+)
- [Bundler](https://bundler.io/) (`gem install bundler`)

## Setup

```sh
bundle install
```

## Development

Start a local server with live reload:

```sh
bundle exec jekyll serve
```

The site will be available at [http://localhost:4000](http://localhost:4000).

## Writing a Post

Add a Markdown file to `_posts/` following the naming convention `YYYY-MM-DD-title.markdown`. Include front matter at the top:

```yaml
---
layout: post
title: "Post Title"
subtitle: "Optional subtitle"
date: 2024-01-01 12:00:00 -0400
excerpt_separator: <!--more-->
---
```

Use `<!--more-->` to mark where the homepage excerpt should end.

## Building for Production

```sh
bundle exec jekyll build
```

Output is generated in the `_site/` directory.

## Project Structure

```
_config.yml     # Site configuration (title, URL, theme, plugins)
_posts/         # Blog posts (Markdown)
_layouts/       # Custom layout overrides (index, post)
_includes/      # Partial templates (head, favicons, etc.)
assets/css/     # SCSS stylesheets
```

## License

[MIT](LICENSE.md)
