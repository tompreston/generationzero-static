# Generation Zero Website (static)
This is a static version of the Gerneration Zero website.

- Old version http://generationzero.org.uk/
- New version (test) https://generationzero-static.onrender.com/
    - I will keep the old URL if we decide to update it like this.

In summary, the new features are:

- Pagination, so we don't show hundreds of posts on the first page.
- Smaller images on the home page (you won't notice).
- Because of the above, 10x faster home page loading.
- Category and author lists:
    - https://generationzero-static.onrender.com/
    - https://generationzero-static.onrender.com/posts/
    - https://generationzero-static.onrender.com/categories/
    - https://generationzero-static.onrender.com/authors/
- I've removed the "Issues" feature since it wasn't used - but it's trivial to
  add back.

It will require a change in workflow, which I need to check with Jake.

## TODO
- [x] Basic clone of site
- [x] Pull cover images
- [x] Pull content images
- [x] Test pull request previews
- [ ] Email Jake
- [ ] Change domain
- [ ] Update Generation Zero main GitHub repo

## Why change backend from Django (dynamic) to Hugo static site generator?
- [Django](https://www.djangoproject.com/)
- [Hugo](https://gohugo.io/).
- [Difference between static and dynamic website](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/What_is_a_web_server)

There are several problems with maintaining the Django backend:
- I forget how to make changes because there's a long time between updates, this
  makes updating the website quite laborious.
- Django updates and changes more often than I update the site, which adds
  unnecessary work.
- The content isn't really dynamic since we only update via the admin interface.
- Deploying the website isn't robust, and prone to mistakes.
- The database is a single file on the web server, and isn't backed up very
  often.
- It's against imgur's TOS to host the images as we are. If they found out,
  they're at liberty to delete all of it.

This new version:
- Simplifies and optimises the website logic by using [Hugo](https://gohugo.io/).
  - For example, the new home page loads 10x faster because images are optimised.
- Easier and cheaper (free!) to deploy using [Render](https://render.com/).
- Implicit data backup because it is stored in GitHub.
- We host the images, so we're not breaking any imgur rules.

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
5. Add a commit summary like "Add my-new-post" and commit to the master branch
   to go live.

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

## Markdown tips
- Instead of using `<br>` tags, you can force new lines by putting two spaces at
  the end of a line.
- Hugo comes with "shortcodes" for figures (images), tweets, instagram, YouTube,
  etc - which you can use instead of HTML tags `<img>` and `<iframes>`.
  [Check them out](https://gohugo.io/content-management/shortcodes/#use-hugos-built-in-shortcodes).

Markdown docs:

- https://daringfireball.net/projects/markdown/
- https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet
- https://www.markdowntutorial.com/
- https://www.markdownguide.org/

YAML docs:

- https://yaml.org/spec/1.2/spec.html#Preview

## License
The artistic content is copyrighted to the respective artists for now, you must
ask permission to use or modify any of it.

We might decide to use a more permissive Creative Commons license in the future:

    https://chooser-beta.creativecommons.org/

The gzer0 theme is MIT.
