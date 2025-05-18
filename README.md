# My Tech Blog

This is a static blog site built with Jekyll that can be deployed on GitHub Pages.

## Features

- Markdown-based blog posts
- Responsive design
- Code highlighting
- Categories for posts
- Easy deployment to GitHub Pages

## Getting Started

### Local Development

1. Install Ruby and Jekyll 
   ```
   gem install bundler jekyll
   ```

2. Clone this repository
   ```
   git clone https://github.com/yourusername/yourusername.github.io.git
   cd yourusername.github.io
   ```

3. Install dependencies
   ```
   bundle install
   ```

4. Run the development server
   ```
   bundle exec jekyll serve
   ```

5. Open your browser at `http://localhost:4000`

### Creating New Posts

To create a new blog post, add a new file to the `_posts` directory with the format:
`YYYY-MM-DD-title-of-post.md`

Include the front matter at the top:

```
---
layout: post
title: "Your Post Title"
date: YYYY-MM-DD
categories: category1 category2
excerpt: "A brief description of your post"
---
```

Then write your post content in Markdown.

### Deploying to GitHub Pages

1. Create a repository named `yourusername.github.io`
2. Push this project to that repository
3. Go to repository settings and enable GitHub Pages
4. Your site will be available at `https://yourusername.github.io`

## Customization

- Edit `_config.yml` to change site settings
- Modify styles in `assets/css/styles.css`
- Update layouts in the `_layouts` directory
