# GeoNum2017-pages
Extracted from https://tiborstanko.sk/teaching/geo-num-2017/

## Dependencies
The site is written in [Jekyll](https://jekyllrb.com/).
Follow the [Jekyll installation guide](https://jekyllrb.com/docs/installation/).

## Setup
```
git clone https://github.com/GeoNumTP/GeoNum2017-pages.git
cd GeoNum2017-pages
bundle exec jekyll serve
# Site now runs at http://localhost:4000
```
## Notes
All pages (index + individual TPs) are included in the root folder. I've also included all stylesheets and scripts necessary to reproduce the look from my website, see [_layouts/default.html](_layouts/default.html).
These are:
- [Bootstrap](https://getbootstrap.com/) for responsive layout
- [Prism.js](https://prismjs.com/) for syntax highlighting
- [MathJax](https://www.mathjax.org/) for displaying math (via external)
- Custom css styles 

Bootstrap and custom styles can be safely disabled, the website should still work fine.
