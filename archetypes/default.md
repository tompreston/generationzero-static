---
authors:
- Jake Ormrod
categories:
- design
- writing
date: {{ .Date }}
resources:
- name: cover
  src: my-cool-cover.jpg
- src: some-other-picture.jpg
title: "{{ replace .Name "-" " " | title }}"
draft: true
---
This is the content of the post.  Front-matter is between the `---` lines.
Remove the line `draft: true` to show the post.

You can upload image "resources" once you've created the post. These must be
listed under `resources:` with a dash `-`.

One of the resources has `name: cover`, and the line underneath `src:` is the
cover image name.  If you remove both of these lines, a text summary will be
displayed instead of a cover image.

The "correct" way to display an image resource is like this:

    {{< figure src="some-other-picture.jpg" title="Some Other Picture" >}}

But you can also use the Markdown syntax like this:

    ![](some-other-picture.jpg "Some Other Picture")

That's it! Delete this content and create a post!
