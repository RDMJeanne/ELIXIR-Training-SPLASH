---
title: Technical documentation
---

This guide explains how to work with the technical infrastructure of SPLASH, including: adding resources, managing tags, running the site locally, and contributing metadata.

## Adding a New Resource

### 1. Create a new resource page

Resources are located in the `pages/resources/` directory. To add a new resource:

1. Navigate to [`pages/resources/`](https://github.com/elixir-europe-training/ELIXIR-Training-SPLASH/tree/main/pages/resources)
2. Copy the [`TEMPLATE_resource_page.md`](https://github.com/elixir-europe-training/ELIXIR-Training-SPLASH/blob/main/pages/resources/TEMPLATE_resource_page.md) file
3. Rename it using lowercase with hyphens aka kebab-case (e.g., `my-new-resource.md`)
4. Fill in the metadata fields (see below)

### 2. Fill in the resource metadata

The frontmatter (metadata) at the top of the file contains all resource information. Here are the key fields:

#### Mandatory fields

```yaml
---
id: unique-resource-id        # Unique identifier, use kebab-case
title: Resource Name           # Display name
resourceUrl: https://example.org/  # Link to the resource
description: |                 # Brief description (can be multiline markdown)
  Short description of the resource
objective: |                   # What the resource aims to achieve
  Main objectives and goals
contributors: [Name One, Name Two]  # List of contributors responsible for the SPLASH resource listing
tags: [elixir, plan, design]   # Resource tags (see Tag System below) - use 3-7 tags
contacts:                      # Contact information
  - name: Contact Name
    email: contact@example.org
---
```

#### Optional but recommended fields

```yaml
mission: |                     # Mission statement (multiline markdown)
  Resource mission
benefit: |                     # Benefits to users (multiline markdown)
  * Benefit 1
  * Benefit 2
logo: resource-logo.svg        # Logo filename (place in assets/img/logos/)
screenshots:                   # Screenshots (place in assets/img/screenshots/)
  - screenshot1.png
  - screenshot2.png
video: https://www.youtube.com/embed/VIDEO_ID  # YouTube embed URL only
publications:                  # Related publications
  - title: Publication title
    url: https://doi.org/...
licenses:                      # License information
  - name: CC BY 4.0
    icon: ccby.png
    url: https://creativecommons.org/licenses/by/4.0/
mailingList: https://...       # Link to mailing list
joinLink: https://...          # Link to join/participate
funding:                       # Funding information
  - name: Funder Name
    logo: funder-logo.png
    url: https://funder.org/
citations: |                   # How to cite the resource
  Citation information
```

### 3. Add resource logo and images

**Logo:**
- Add logo file to [`assets/img/logos/`](https://github.com/elixir-europe-training/ELIXIR-Training-SPLASH/tree/main/assets/img/logos)
- Use SVG format when possible
- Reference in frontmatter: `logo: your-logo.svg`

**Screenshots:**
- Add screenshots to [`assets/img/screenshots/`](https://github.com/elixir-europe-training/ELIXIR-Training-SPLASH/tree/main/assets/img/screenshots)
- Use descriptive filenames
- List in frontmatter under `screenshots:`

### 4. Add resource content

After the frontmatter, you can add the other content of the resource page using Markdown. Structure your content with clear headings:

```markdown
---
# frontmatter here
---

## Additional Information

More detailed information about the resource.
```

### 5. Add contributors to CONTRIBUTORS.yml

Ensure all contributors listed in the resource metadata are also in [`_data/CONTRIBUTORS.yml`](https://github.com/elixir-europe-training/ELIXIR-Training-SPLASH/blob/main/_data/CONTRIBUTORS.yml):

```yaml
Name Surname:
  git: github_username
  email: email@example.com
  orcid: 0000-0000-0000-0000
  affiliation: Institution Name
```
(The 'role' key is only used for editorial team members)

## Tag System for Resources

The tag system allows you to categorize resources with colored badges that appear on resource cards. Tags are centrally managed in `_data/resource_tags.yml` to ensure consistency across the site.

### Understanding Tags and Categories

Tags are organized into categories defined in `_data/tag_categories.yml`. Each category has an associated color that applies to all tags within that category.

**Common categories:**
- **Organization** - Resources affiliated with specific organizations or collaborative networks
- **Node** - Resources that are in the service delivery plan of a specific node
- **Lifecycle** - Training development phases (Plan, Design, Develop, Deliver, Evaluate)
- **Topic** - Subject areas and themes covered by the resource

**Tag system files:**
- [`_data/resource_tags.yml`](https://github.com/elixir-europe-training/ELIXIR-Training-SPLASH/blob/main/_data/resource_tags.yml) - All available tags
- [`_data/tag_categories.yml`](https://github.com/elixir-europe-training/ELIXIR-Training-SPLASH/blob/main/_data/tag_categories.yml) - Category definitions with colors

### Adding Tags to a Resource

In the frontmatter of any resource page (e.g., `pages/resources/your-resource.md`), add a `tags` field with an array of tag IDs:

```yaml
---
id: your-resource
title: Your Resource Name
tags: [elixir, plan, design, fair-training]  # Use 3-7 tags for clarity
# ... other fields ...
---
```

### Managing Tags

#### Adding New Tags

To add a new tag to the system:

1. Open `_data/resource_tags.yml`
2. Add a new entry following this format:

```yaml
- id: your-tag-id           # Use kebab-case, no spaces
  label: Display Name       # How it appears on cards
  category: topic           # organization, node, lifecycle, topic, etc.
  description: Tooltip text # Optional: shown on hover
```

**Note:** The tag's color is automatically determined by its category (defined in `_data/tag_categories.yml`). All tags within the same category share the same color.

#### Adding a New Category

To create an entirely new category:

1. Open `_data/tag_categories.yml`
2. Add a new entry:

```yaml
- id: yourcategory          # Use kebab-case, matches the category field in tags
  label: Your Category      # Display name (shown in uppercase on resources page)
  description: Explanation of what this category represents
  color: primary            # Bootstrap color - all tags in this category use this
```

**Available Bootstrap colors:**
- `primary` - Aubergine/purple (default theme color)
- `secondary` - Gray
- `success` - Green
- `danger` - Red
- `warning` - Orange/Yellow
- `info` - Light blue
- `light` - Light gray
- `dark` - Dark gray/black

The category will automatically appear on the resources page in the order defined in `tag_categories.yml`.

### Best Practices

1. **Limit tags per resource**: Use 3-7 tags for clarity
2. **Use consistent categories**: Include at least one organization or lifecycle tag
3. **Category colors**: Choose colors that visually distinguish categories
4. **Descriptive labels**: Keep labels short (1-3 words) but clear
5. **Meaningful descriptions**: Add helpful tooltip text for less obvious tags

### Where Tags Are Used

**Resources Page:**
- Filter sidebar with all tags organized by category
- Tags are searchable via the search box
- Click a tag to filter; click again to deselect
- Tags displayed on each resource card (in order defined in `resource_tags.yml`)

**Home Page Carousel:**
- Only shows resources tagged with `elixir`
- Displays only lifecycle tags on cards (organization, node, and topic tags are hidden)
- Randomized order on each build

**Lifecycle Pages (Plan, Design, Develop, Deliver, Evaluate):**
- Automatically displays resources tagged with the corresponding lifecycle tag
- Shows full resource cards with logos, titles, and tags

### Technical Implementation

**Reusable component:** `_includes/related-resources.html`

```liquid
{% raw %}{% include related-resources.html tag="plan" %}{% endraw %}
```

This component filters resources by tag and displays cards with logos, titles, and tag badges. It's used on all lifecycle pages.

**Tag ordering:** Tags are displayed in the order they appear in `_data/resource_tags.yml`, NOT alphabetically.

**Filtering behavior on resources page:**
- Clicking a tag filter shows only resources with that tag
- Clicking the same tag again deselects it (returns to "All Resources")
- The "All Resources" button always shows all resources
- Search works in combination with tag filters

## Running the Site Locally

### Option 1: Using Docker (Recommended)

This repository includes Docker configuration for running the site without installing Ruby, Jekyll, or gems on your machine.

**Prerequisites:** Docker Desktop (or any recent Docker Engine) installed and running.

**Quick start:**

```bash
# Build the Jekyll image (use --no-cache for a clean rebuild)
docker compose build jekyll

# Start the service
docker compose up -d jekyll

# Watch the server start and rebuilds
docker compose logs --tail=200 --follow jekyll
```

Once the container reports "Server address: http://0.0.0.0:4000", open [http://localhost:4000](http://localhost:4000) in your browser.

**Notes:**
- If you change `Gemfile` or `Gemfile.lock`, rebuild the image: `docker compose build jekyll`
- The repository is mounted into the container, so file edits trigger automatic Jekyll regeneration
- Use `Ctrl+C` to stop following logs, or `docker compose down` to stop and remove the container

### Option 2: Native Jekyll (Without Docker)

Run Jekyll directly on macOS/Linux without Docker.

**Prerequisites:**

1. **Ruby 2.7.0 or higher:**
   ```bash
   # Check Ruby version
   ruby -v
   
   # Install Ruby via Homebrew (macOS)
   brew install ruby
   ```

2. **Bundler:**
   ```bash
   gem install bundler
   ```

**Running the site:**

1. **Install dependencies:**
   ```bash
   bundle install
   ```

2. **Start the Jekyll server:**
   ```bash
   bundle exec jekyll serve
   ```

3. **Open in browser:** Navigate to [http://localhost:4000](http://localhost:4000)

The server automatically rebuilds when you make changes. Press `Ctrl+C` to stop.

**Troubleshooting:**
- **Ruby version**: Ensure Ruby 2.7+ is installed (`ruby -v`)
- **Native extensions**: Install Xcode Command Line Tools if needed: `xcode-select --install`
- **Port conflict**: Use a different port: `bundle exec jekyll serve --port 4001`

## Website File Structure

### Directory Organization

* **Content pages**: [`pages/`](https://github.com/elixir-europe-training/ELIXIR-Training-SPLASH/tree/main/pages) directory
  * Resources: `pages/resources/`
  * Contribute: `pages/contribute/`
  * Lifecycle: `pages/lifecycle/`
  * About: `pages/about/`
* **Sidebar navigation**: [`_data/sidebars/`](https://github.com/elixir-europe-training/ELIXIR-Training-SPLASH/tree/main/_data/sidebars)
* **Contributors metadata**: [`_data/CONTRIBUTORS.yml`](https://github.com/elixir-europe-training/ELIXIR-Training-SPLASH/blob/master/_data/CONTRIBUTORS.yml)
* **Tag system**:
  * [`_data/resource_tags.yml`](https://github.com/elixir-europe-training/ELIXIR-Training-SPLASH/blob/main/_data/resource_tags.yml)
  * [`_data/tag_categories.yml`](https://github.com/elixir-europe-training/ELIXIR-Training-SPLASH/blob/main/_data/tag_categories.yml)
* **Assets**: `assets/img/`
  * Logos: `assets/img/logos/`
  * Screenshots: `assets/img/screenshots/`

### Markdown File Naming

* Use lowercase with hyphens (kebab-case) for new files: `my-new-page.md`
* Ensure unique filenames across the entire site
* File `example.md` renders at `https://elixir-europe-training.github.io/ELIXIR-Training-SPLASH/example`

### Managing Sidebar Navigation

Edit the relevant `.yml` file in [`_data/sidebars/`](https://github.com/elixir-europe-training/ELIXIR-Training-SPLASH/tree/main/_data/sidebars) to add or modify menu items:

```yaml
- title: Level_1_title
  url: /page_name
  subitems:
    - title: Level_2_title
      url: /subpage_name
```

**Attributes:**
* `title`: Display text in sidebar
* `url`: Internal page path (e.g., `/example`)
* `external_url`: Use for external links instead of `url`
* `subitems`: Create hierarchy levels

**Available sidebar files:**
* `main.yml` - Main site navigation
* `contribute.yml` - Contribute section
* `lifecycle.yml` - Lifecycle pages
* `about.yml` - About section

## Page Metadata Reference

All pages require metadata (frontmatter) at the top of the Markdown file. Here are the key fields:

### Required fields for all pages

```yaml
---
title: Page Title              # Display name
---
```

### Recommended fields

```yaml
---
title: Page Title
description: Brief description of the page content  # Used in search and previews
contributors: [Name One, Name Two]  # List of contributors
---
```

### Optional fields

```yaml
---
title: Page Title
description: Brief description
contributors: [Name One, Name Two]
page_id: unique-page-id        # Unique identifier for cross-referencing
search_exclude: true           # Exclude from site search (use sparingly)
summary: Short summary text    # Displayed in some contexts
related_pages:                 # Related pages shown at bottom
  - plan
  - design
training:                      # Training materials
  - name: Training Name
    url: https://example.org
affiliation: Institution       # Contributing institution
---
```

### Resource-specific metadata

For resource pages in `pages/resources/`, see the [Adding New Resources](#adding-a-new-resource) section above for the complete metadata reference.

**Important:**
- All contributors must be listed in [`_data/CONTRIBUTORS.yml`](https://github.com/elixir-europe-training/ELIXIR-Training-SPLASH/blob/main/_data/CONTRIBUTORS.yml)
- Use kebab-case for IDs (lowercase with hyphens)
- The `page_id` should be unique across the site - check existing IDs in the metadata at the top of markdown files
- See the [ELIXIR Toolkit Theme page mechanics guide](https://elixir-belgium.github.io/elixir-toolkit-theme/page_mechanics) for advanced metadata options

## Contributing to CONTRIBUTORS.yml

All contributors listed in page metadata should be added to [`_data/CONTRIBUTORS.yml`](https://github.com/elixir-europe-training/ELIXIR-Training-SPLASH/blob/main/_data/CONTRIBUTORS.yml) to enable proper attribution and linking.

1. Open [`_data/CONTRIBUTORS.yml`](https://github.com/elixir-europe-training/ELIXIR-Training-SPLASH/blob/main/_data/CONTRIBUTORS.yml)
2. Add your entry in alphabetical order by last name:

```yaml
Name Surname:
  git: github_username         # Your GitHub username (without @)
  email: name@example.com      # Contact email
  orcid: 0000-0000-0000-0000   # ORCID identifier (optional but recommended)
  affiliation: Institution     # Your institution or organization
```

**Notes:**
- All fields except `role` are recommended for proper attribution
- The `role` field can be used to specify editorial team members
- Your entry enables linkage to your GitHub profile, ORCID, and email on the [contributors page](https://elixir-europe-training.github.io/ELIXIR-Training-SPLASH/contributors)
- Ensure your name matches exactly how you list yourself in page metadata
