# GitHub Pages `.github/readme.md`

In this repository I test whether a GitHub repository with GitHub Pages enabled
will use `.github/readme.md` instead of `readme.md` when rendering the GitHub
Pages site.

`github/readme.md` is a feature of GitHub allowing to override the readme used
to render on the repository main page on GitHub.

https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-readmes

> If you put your README file in your repository's hidden `.github`, `root`, or
> `docs` directory, GitHub will recognize and automatically surface your README
> to repository visitors.

> If a repository contains more than one README file, then the file shown is
> chosen from locations in the following order: the `.github` directory, then
> the repository's `root` directory, and finally the `docs` directory.

I wonder how these variants play with the GitHub Pages Jekyll-based renderer
which uses the https://github.com/benbalter/jekyll-readme-index plugin to make
it so that the Jekyll static site generator uses `README.md` over `index.md` as
the directory's index file.

I enabled GitHub Pages for this repository, the site can be found here:
https://tomashubelbauer.github.io/github-pages-dotgithub-readme/

And the GitHub Actions workflow that builds the deploys the site here:
https://github.com/TomasHubelbauer/github-pages-dotgithub-readme/actions/workflows/pages/pages-build-deployment

| File(s) | GitHub repository page picks | GitHub Pages site picks |
|-|-|-|
| `README.md` | `README.md` | `README.md` |
| `README.md`, `.github/README.md` | `.github/README.md` | `README.md` |

Note that I am not enumerating all possible configurations here, only the ones I
care about.

The reason the `.github/README.md` override README wasn't used is because the
plugin GitHub Pages uses doesn't implement this:

https://github.com/benbalter/jekyll-readme-index/blob/master/lib/jekyll-readme-index/generator.rb

```ruby
# Regexp to match a file path against to detect if the given file is a README
def readme_regex
  @readme_regex ||= %r!/readme(#{Regexp.union(markdown_converter.extname_list)})$!i
end
```

I've requested this feature be added to the Jekyll plugin GitHub Pages uses:

https://github.com/benbalter/jekyll-readme-index/issues/38
