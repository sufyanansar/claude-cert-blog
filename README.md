# Claude Certification Journal

A team blog built with Jekyll and hosted free on GitHub Pages. There's no server and no build step.

## Setup (one time)
1. Create a GitHub repo named `claude-cert-blog` and push this folder to it.
2. In `_config.yml`, replace `YOUR-GITHUB-USERNAME` (in two places) with your GitHub username. Do the same in `_data/authors.yml`.
3. In the repo, go to **Settings → Pages → Build and deployment → Deploy from a branch → `main` / `(root)`**.
4. After about a minute the site is live at `https://<user>.github.io/claude-cert-blog/`.
5. Add each teammate as a collaborator (**Settings → Collaborators**) and add them to `_data/authors.yml`.

## Publishing a post
- **Team members:** use **Submit a post** on the site. The post is emailed to the admin (through formsubmit.co), who checks it and saves the `markdown_file` text as the `save_as` path in `_posts/`.
- **Manual way:** copy `_templates/post.md` to `_posts/YYYY-MM-DD-my-title.md` and commit.

Categories are Progress, Findings and Research. To change them, edit `categories_list` in `_config.yml`.
