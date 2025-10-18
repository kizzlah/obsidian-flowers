2025-09-23

- Append a line to the site configuration file, indicating the current theme.

```
echo "theme = 'ananke'" >> hugo.toml
```

- Start Hugo’s development server to view the site.

```
hugo server
```
- Press Ctrl + C to stop Hugo’s development server.

###### Add content

- add new page 

```
hugo new content content/posts/my-first-post.md
```

- hugo creates the file in the content/posts directory. 

```
+++
title = "My First Post"
date = 2024-01-14
draft = true
```
- Notice the draft value in the front matter is true. By default, Hugo does not publish draft content when you build the site. Learn more about draft, future, and expired content.

- Add some Markdown to the body of the post, but do not change the draft value.

```
+++
title = "My First Post"
date = 2025-09-23 19:53
draft = true
+++
## Introduction 

**bold**
*italics*
```

- Save the file, then start Hugo’s development server to view the site. You can run either of the following commands to include draft content.

```
hugo server --buildDrafts
hugo server -D
```

- View your site at the URL displayed in your terminal. Keep the development server running as you continue to add and change content.

- when satisfied with whatever edits are to be made, set the front matter **draft** parameter to false.

