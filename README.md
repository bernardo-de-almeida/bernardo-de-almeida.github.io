# Personal Website - Bernardo P. de Almeida

Personal website hosted on GitHub Pages at [bernardo-de-almeida.github.io](https://bernardo-de-almeida.github.io)

## Technology Stack

- **Jekyll** - Static site generator (GitHub Pages native)
- **Liquid** - Template engine
- **YAML** - Data files for content management
- **HTML/CSS** - Frontend (same visual design as original)

## Quick Start

### Prerequisites

- Ruby 3.1.x (required for GitHub Pages compatibility)
- Bundler

### Local Development

```bash
# Install dependencies
bundle install

# Build the site
bundle exec jekyll build

# Serve locally at http://localhost:4000
bundle exec jekyll serve
```

## Project Structure

```
_config.yml           # Jekyll configuration
_layouts/             # Page layouts
_includes/            # Reusable components (navigation, footer, templates)
_data/                # YAML data files (publications, news, etc.)
assets/               # CSS, images, PDFs
index.html            # Homepage
publications/         # Publications page
code/                 # Code page
about/                # About page
tutorials/            # Tutorials page
```

## Documentation

- [CONTRIBUTING.md](CONTRIBUTING.md) - Guide for adding content
- [Jekyll Documentation](https://jekyllrb.com/docs/)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)

## License

Personal website content © Bernardo P. de Almeida
