# Generation Zero Website (static)
This is a static version of http://generationzero.org.uk/

## TODO
- [x] Basic clone of site
- [x] Pull cover images
- [x] Pull content images
- [ ] Test new pages
- [ ] Change domain
- [ ] Email Jake

## Why change backend from Django to Hugo static site generator?
There are several problems with maintaining the Django backend:
- I forget how to make changes because there's a long time between updates.
- Django updates (changes) more often than I update the site, which adds
  unnecessary work.
- The content isn't really dynamic since we only update via the admin interface.
- Deploying the website isn't robust, and prone to mistakes.
- The database is a single file on the web server, and isn't backed up very often.
- It's against imgur's TOS to host the images as we are.

This new version:
- Simplifies and optimises the website logic by using [Hugo](https://gohugo.io/).
- Easier and cheaper (free?) to deploy using [Render](https://render.com/).
- Implicit data backup because it is stored in GitHub.
- Self-hosting images, so we're not breaking any rules.

The change will require a change in workflow when updating content. Instead of
adding *entries* to the admin interface, now we add *posts* to GitHub. Render
supports website previews using GitHub Pull Requests. I will document this
below.

## Adding a new post to Generation Zero static
Posts are directories in `content/posts`. The directory name is the post slug.
The post directories contain two things:

1. `index.md`, this is the actual content and Hugo "front matter" (see below)
2. Resources like image files (png, jpg)

To add a new post:

1. Using the GitLab web interface, go to `content/posts`.
2. Click "Add file" > "Create new file", call it `my-new-post/index.md`.
3. Add the content "front matter" sandwiched in between two `---` lines, and
   the post content in Markdown. See the example below.
4. Upload any image resources with "Add file" > "Upload files" and reference
   them in the front matter. It doesn't matter what they're called.
5. Add a commit summary like "Add my-new-post" and either commit to the master
   branch (go live!) or create a "new branch" start a pull-request (preview).

```
---
authors:
- Thomas Preston
categories:
- design
- writing
date: 2020-07-31
resources:
- name: cover
  src: my-cool-cover.jpg
- src: some-other-picture.jpg
title: This is a new post!
---
Hi, this is the new content layout!

One of the resources has a `name: cover`. If you remove this, a text summary
will be displayed instead.

The "correct" way to display images with Hugo content is like this:

    {{< figure src="some-other-picture.jpg" title="Some Other Picture" >}}

But you can also use the Markdown syntax like this:

    ![](some-other-picture.jpg "Some Other Picture")
```

- The format for the "front matter" is called YAML.
- The format for the content is called Markdown.

## License
The artistic content is copyrighted to the respective artists for now, you must
ask permission to use or modify any of it.

We might decide to use a more permissive Creative Commons license in the future:

    https://chooser-beta.creativecommons.org/

The gzer0 theme is MIT.
