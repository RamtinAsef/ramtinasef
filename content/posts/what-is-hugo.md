+++
title = 'What Is Hugo'
date = 2024-02-08T22:10:56+01:00
draft = false
+++

Hugo is simple, easy to work with, and fast.

It's an open-source static site generator allowing content written in plain text files (*markup files*) into fully functional websites.

There are a ton of good tutorials online on how to get started and as mentioned in this post [Follow Up On First Post](/content/posts/follow-up-on-first-post.md "Follow Up On First Post").

The [Hugo documentation](https://gohugo.io/documentation/ "Hugo Docs") is very straightforward.

Once you've setup your initial Hugo site, you'll notice that the structure is quite simple. You have *archetypes*, *content*, *data*, *layouts*, *static*, *themes* and *config* and I'll just briefly go through each of them.

**_archetypes_**: Templates for creating new content with consistent structure and metadata.

**_content_**: Main folder for storing text and assets representing your website's pages and posts.

**_data_**: Holds structured data files used for configuration and content that doesn't belong in the main content folders.

**_layouts_**: Contains template files that define how your content is displayed on the website.

**_static_**: Stores static assets like images, CSS, and JavaScript files that are served directly to visitors.

**_themes_**: Where you install and manage pre-designed themes that define the website's appearance.

**__config_**: The configuration file (e.g., config.toml) with site settings and parameters.

So if I would like to change the content-template, I would go to the *default.md*-file inside the *archetypes*-folder and configure this:

```
+++
title = '{{ replace .File.ContentBaseName "-" " " | title }}'
date = {{ .Date }}
draft = true
+++

```

to fx:

```
+++
title = '{{ replace .File.ContentBaseName "-" " " | title }}'
date = {{ .Date }}
tags = ["webdevelopment", "coding"]
draft = false
+++

```

defaulting all created content to not being draft and also defaulting their tags. Just to share an example.