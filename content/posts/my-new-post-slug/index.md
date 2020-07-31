---
authors:
- Thomas Preston
categories:
- design
- writing
date: 2020-07-31
resources:
- src: my-cool-cover.jpg
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
