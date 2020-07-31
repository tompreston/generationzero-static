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

## License
The artistic content is copyrighted to the respective artists for now, you must
ask permission to use or modify any of it.

We might decide to use a more permissive Creative Commons license in the future:

    https://chooser-beta.creativecommons.org/

The gzer0 theme is MIT.
