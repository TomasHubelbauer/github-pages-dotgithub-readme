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

| File(s) | GitHub repository page picks | GitHub Pages site picks |
|-|-|-|
| `README.md` | `README.md` | `README.md` |
| `README.md`, `.github/README.md` | TODO | TODO |
| `README.md`, `docs/README.md` | TODO | TODO |
| `README.md`, `root/README.md` | TODO | TODO |

Note that I am not enumerating all possible configurations here, only the ones I
care about.
