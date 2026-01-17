# Contributing to the Website

This website is built with Jekyll and uses YAML data files to manage content. This makes it easy to add publications, news, and other content without editing HTML.

## Prerequisites

- Ruby 3.1.x (required for GitHub Pages compatibility)
- Bundler

### Installing Ruby 3.1

**macOS (using Homebrew):**
```bash
brew install ruby@3.1
export PATH="/opt/homebrew/opt/ruby@3.1/bin:$PATH"
```

**Other platforms:**
See https://www.ruby-lang.org/en/documentation/installation/

## Local Development

### Initial Setup

1. Install dependencies:
```bash
bundle install
```

2. Build the site:
```bash
bundle exec jekyll build
```

3. Serve the site locally:
```bash
bundle exec jekyll serve
```

Then visit http://localhost:4000 in your browser.

## Adding Content

### Adding a New Publication

Edit `_data/publications.yml` and add your publication to the appropriate section (`selected`, `preprints`, `others`, `workshop_papers`, `phd_thesis`, or `softwares`).

**Example:**
```yaml
selected:
  - id: "26"  # Increment the ID
    authors: "<strong>B.P. de Almeida</strong>, Co-Author Name, ..."
    title: "Your Paper Title"
    journal: "Nature"
    year: 2026
    url: "https://www.nature.com/articles/..."
    code: "https://github.com/your-username/repo"  # Optional
    model: "https://huggingface.co/..."  # Optional
    data: "https://zenodo.org/..."  # Optional
    image: "/assets/images/your-paper-image.png"  # Optional
    preprint: "https://biorxiv.org/..."  # Optional
    featured_commentary:  # Optional
      - author: "Author Name"
        text: "Commentary Title"
        journal: "Journal Name Year"
        url: "https://..."
    press:  # Optional
      - text: "Press release title"
        url: "https://..."
    video: "https://www.youtube.com/embed/VIDEO_ID"  # Optional
```

**Available Fields:**
- `id` (required): Publication number as a string (e.g., "26")
- `authors` (required): Author list (use `<strong>` for your name)
- `title` (required): Paper title (can include `<em>` for italics)
- `journal` (required): Journal name
- `year` (required): Publication year
- `url` (required): Link to the paper
- `code`: Link to GitHub repository
- `model`: Link to model (HuggingFace, Kipoi, etc.)
- `data`: Link to data (Zenodo, GEO, etc.)
- `benchmark`: Link to benchmark dataset
- `geo`: Link to GEO accession
- `preprint`: Link to preprint
- `image`: Path to image (single image)
- `images`: List of image paths (for multiple images)
- `featured_commentary`: List of commentaries
- `press`: List of press releases
- `video`: YouTube embed URL

### Adding News

Edit `_data/news.yml` and add your news item at the **top** of the file (most recent first).

**Example 1: Simple news with inline links:**
```yaml
- date: "2026-01"
  text: 'Excited to present our work at <a href="https://..." class="link">Conference Name</a> (January 2026)'
```

**Example 2: Award announcement with image:**
```yaml
- date: "2026-05"
  text: 'Very happy to receive <a href="https://..." class="link">Award Name</a> for outstanding research (May 2026)'
  images:
    - "/assets/images/award-photo.png"
```

**Example 3: News with additional details:**
```yaml
- date: "2026-04"
  text: 'Presented our work at <a href="https://..." class="link">Conference Name</a> (April 2026)'
  additional_text: '. For more information see <a href="https://..." class="link">here</a>'
```

**Example 4: News with video:**
```yaml
- date: "2026-03"
  text: 'Check my talk on <a href="https://..." class="link">Topic Name</a> (March 2026)'
  video: "https://www.youtube.com/embed/VIDEO_ID"
```

**Available Fields:**
- `date` (required): Date in "YYYY-MM" format
- `text` (required): News text with embedded HTML links using `<a href="..." class="link">` tags
- `additional_text` (optional): Additional details in smaller font (typically starts with ". ")
- `images` (optional): List of image paths
- `video` (optional): YouTube embed URL

**Important**: Use single quotes around text fields to avoid YAML escaping issues with HTML.

### Adding Research Highlights

Edit `_data/research_highlights.yml` to feature important publications on the homepage.

**Example:**
```yaml
- title: "Your Important Paper Title"
  journal: "Nature"
  year: 2026
  url: "https://..."
  description: "Brief description of the work and its significance."
  image: "/assets/images/paper-figure.png"
  press:
    - text: "Press release title"
      url: "https://..."
  video: "https://www.youtube.com/embed/VIDEO_ID"  # Optional
```

### Updating Site Information

Edit `_data/site_info.yml` to update your bio, title, or contact information:

```yaml
name: "Your Name"
title: "Your Job Title"
bio: "Your bio text..."
photo: "/assets/images/your-photo.png"
email: "your@email.com"
# ... etc
```

## Deployment

### Deploying to GitHub Pages

The site automatically builds and deploys when you push to the `master` branch:

```bash
git add .
git commit -m "Add new publication"
git push origin master
```

GitHub Pages will automatically build and deploy the site using Jekyll.

## Project Structure

```
bernardo-de-almeida.github.io/
├── _config.yml              # Jekyll configuration
├── _layouts/
│   └── default.html         # Base layout (navigation + footer)
├── _includes/
│   ├── navigation.html      # Site navigation
│   ├── footer.html          # Site footer
│   ├── publication.html     # Publication template
│   ├── news-item.html       # News item template
│   └── research-highlight.html  # Research highlight template
├── _data/
│   ├── publications.yml     # ✏️ Edit to add publications
│   ├── news.yml            # ✏️ Edit to add news
│   ├── research_highlights.yml  # ✏️ Edit to add highlights
│   └── site_info.yml       # ✏️ Edit to update bio/contact
├── assets/
│   ├── css/main.css        # Site styles
│   └── images/             # Images directory
├── index.html              # Homepage (Jekyll template)
├── publications/index.html  # Publications page (Jekyll template)
├── code/index.html         # Code page (Jekyll template)
├── about/index.html        # About page (Jekyll template)
├── tutorials/index.html    # Tutorials page (Jekyll template)
├── Gemfile                 # Ruby dependencies
└── CONTRIBUTING.md         # This file
```

## Tips

1. **Always use double quotes** in YAML files for string values
2. **IDs must be strings**, not numbers (use `"26"` not `26`)
3. **Test locally** before pushing to GitHub:
   ```bash
   bundle exec jekyll serve
   ```
4. **Validate YAML syntax** using an online YAML validator if you get errors
5. **Images should be placed** in `/assets/images/`
6. **Keep backups** of your YAML files before making major changes

## Troubleshooting

### Build Errors

If Jekyll fails to build:

1. Check YAML syntax (common issues: missing quotes, incorrect indentation)
2. Ensure Ruby 3.1.x is being used
3. Run `bundle exec jekyll build` to see detailed error messages

### Content Not Showing

1. Verify the YAML file is saved
2. Check that indentation is correct (use spaces, not tabs)
3. Rebuild the site: `bundle exec jekyll build`

### Ruby Version Issues

This site requires Ruby 3.1.x due to GitHub Pages compatibility. Ruby 3.2+ has breaking changes with the Liquid template engine.

To use the correct Ruby version:
```bash
export PATH="/opt/homebrew/opt/ruby@3.1/bin:$PATH"
```

## Questions?

If you encounter issues or have questions, please open an issue on GitHub or consult the [Jekyll documentation](https://jekyllrb.com/docs/).
