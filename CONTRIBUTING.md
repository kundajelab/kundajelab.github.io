The theme is based off of [al-folio](https://github.com/alshedivat/al-folio), so please refer to their repo (particularly INSTALL.md and CUSTOMIZE.md) for more information.

# Previewing the site locally

I recommend setting this up as it is very helpful if you want to quicklu test out your local changes before pushing them to the live site. You can either use Docker containers as outlined [here](https://github.com/alshedivat/al-folio/blob/main/INSTALL.md) or install Ruby and Jekyll locally. I describe the steps to do the latter below.

1. Install **rbenv** via brew, as described [here](https://github.com/rbenv/rbenv).
2. Install the latest ruby version as shown on the official Ruby website.
3. Run `rbenv global <the version you installed>`.
4. Run `ruby -v` to confirm you have the new ruby installed. If not, you might want to do `rbenv rehash`.
5. `cd` into the local directory containing the website code, which you'll have cloned from this repo.
6. Create a new conda env and inside it install **imagemagick** with conda (see [here](https://anaconda.org/conda-forge/imagemagick)) and **jupyter** with pip (as shown on PyPI).
7. In this conda env, run `which ruby` to confirm the ruby version is the one you installed in step 3.
8. Run `gem install bundler` then `bundle install`.
9. Run `gem install jekyll`.
10. Run `bundle exec jekyll serve --watch`. You might want to do `bundle exec jekyll clean` before.
11. It should populate the \_site directory at the root of the repo, and also show you the localhost link where to access the site. If it does not, you might need to explicitly provide an open local port, e.g., `bundle exec jekyll serve --port 5000 --watch`.
12. You can now edit local files and see the changes reflected on the local site.
13. If you change the `_config.yml` file, you need to re-run `bundle exec jekyll serve`, and also might want to run `bundle exec jekyll clean` before that.

# Deploying changes to the site

1. Make sure you have the latest version of the repo.
2. Create a new branch with `git checkout -b <your branch name>`.
3. Make your changes locally and preferably preview them locally (see below).
4. Commit changes and push to **your branch**.
5. Open a pull request to the main branch of the repo.
6. **Be sure that all PR checks pass**. Once that is done, merge the PR.
    - You may find that the "Prettier" check often fails. For this, I highly recommend installing **prettier** locally and running `prettier --write .` in the root of the repo. This will automatically format all files in the repo, and you can then commit and push those changes.
7. The deployment GitHub action is automatically triggered upon push to main and your changes will be live on the website once the action finishes running successfully.

# Adding a new profile

1. Create a new `about_<person>.md` file in the `_pages/profiles` directory, following the template specified in `_pages/profiles/template.md`.
2. Add a profile picture under `assets/img/profile_pics`.
3. Edit `_pages/profiles.md` to add the new profile to the list of profiles. Like so:

```markdown
profiles:
<other profiles...>

- align: left
  image: <profile pic name>.jpg
  content: profiles/about\_<person>.md
```

# Adding a new blog post

Create a new markdown file in the `_posts` directory. There are several blog post templates and examples [here](https://github.com/alshedivat/al-folio/tree/main/_posts). Make sure to preview your changes as described above before pushing them to the live site.

# Adding a new publication

Edit `_bibliography/papers.bib`.
