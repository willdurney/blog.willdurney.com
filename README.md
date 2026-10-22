# blog.willdurney.com

Source for [Prattle of Will's](https://blog.willdurney.com), Will Durney's personal blog about tech, pop culture, and the world. It's a static site built with [Jekyll](https://jekyllrb.com/) 4 and the [Hydeout](https://github.com/fongandrew/hydeout) theme.

## Requirements

- **Ruby 3.4.** The exact version is pinned in [`.ruby-version`](.ruby-version), so a version manager like [rbenv](https://github.com/rbenv/rbenv) picks it up automatically. Ruby 4 won't work yet: Hydeout 5.0.2 requires Ruby `~> 3.0`.
- **[Bundler](https://bundler.io/) 4.** The version that wrote the lockfile is listed under `BUNDLED WITH` in [`Gemfile.lock`](Gemfile.lock).

## Getting started

```sh
rbenv install --skip-existing   # installs the Ruby from .ruby-version
gem install bundler
bundle install
bundle exec jekyll serve
```

The site is served at <http://localhost:4000> and rebuilds when files change. Changes to `_config.yml` are not picked up by the watcher, so restart the server after editing it.

## Writing a post

Add a Markdown file to `_posts/` named `YYYY-MM-DD-slug.markdown`, starting with front matter:

```yaml
---
layout: post
title: 'Post Title'
subtitle: 'Optional subtitle'   # shown under the title on the post and the home page
date: 2026-01-01 12:00:00 -0400
excerpt_separator: <!--more-->
---
```

- Titles and subtitles are rendered as Markdown, so `*emphasis*` works. Asterisks are stripped from the browser tab title.
- Put `<!--more-->` where the home page excerpt should end. If the post is longer than the excerpt, the home page adds a "More…" link.
- To preview a post without publishing it, put it in `_drafts/` (no date in the file name) and run `bundle exec jekyll serve --drafts`.

## Building

```sh
JEKYLL_ENV=production bundle exec jekyll build
```

`JEKYLL_ENV=production` turns on the Google Analytics snippet, which Hydeout leaves out of development builds. The site is written to `_site/`, which is git-ignored. The output is plain static files and can be hosted anywhere. The live site is served from shared web hosting, and there's no automated deploy, so publishing means uploading the contents of `_site/` to the host.

## Project structure

```
_config.yml           Site settings: title, URL, theme, plugins, pagination, Disqus, analytics
_posts/               Published posts (Markdown)
_layouts/             Overrides of Hydeout's index and post layouts, adding subtitle support
_includes/            Overrides of Hydeout partials (head, favicons, sidebar copyright line; related posts are turned off)
assets/css/main.scss  Theme stylesheet entry point; sets the sidebar color and subtitle styles
404.html              Not-found page
index.html            Home page, a paginated list of posts (5 per page)
```

Hydeout's own layouts and includes come from the `jekyll-theme-hydeout` gem. Any file with the same path in this repo overrides the theme's version. To see the originals, run `bundle info --path jekyll-theme-hydeout`.

## Configuration

Site-wide settings live in [`_config.yml`](_config.yml):

| Setting | Purpose |
| --- | --- |
| `title`, `tagline`, `description` | Shown in the sidebar and page titles |
| `url` | Canonical site URL, used for absolute links and the feed |
| `paginate` | Number of posts per home page (`jekyll-paginate`, bundled with Hydeout) |
| `disqus.shortname` | Enables Disqus comments on posts |
| `google_analytics` | Analytics property ID, included only in production builds |

The Atom feed is generated at `/feed.xml` by [jekyll-feed](https://github.com/jekyll/jekyll-feed).

## Updating dependencies

```sh
bundle update --all
bundle exec jekyll build   # check that the site still builds cleanly
```

## License

[MIT](LICENSE.md)
