# Markdown Content

All the markdown content needed for our website to run. The repo is divided in 2 parts, `guides` and `other`. It follows the following structure:

```
├── guides
│   └── Section Name (in English)
│       └── 1. Guide Name (in English)
│           └── locale.md
└── other
    └── Page Name
        └── locale.md
```

## Guides

### Sections
The guides page is structured in sections, and there can be many sections. In this case `FAQs` and `Map-making` are sections: 

![](https://i.imgur.com/JHgs00F.gif)

It is important to mention that the title of sections and guides has to be *in English*. It will be translated later on the website by adding the corresponding keys.

### Guides (the actual guides themselves)
Each guide is inside a section, and a section may have many guides, which are ordered by using a number, a dot and then a space, like such:

![](https://i.imgur.com/iprAG4u.png)

And this is how it is displayed on the website:

![](https://i.imgur.com/kE0MOV6.png)

Each guide, then, is not a file by itself but rather inside a folder with its name. That is because each guide has to be translated to several languages used on the website, such as English or Spanish. That is accomplished by distinguishing several files by their short, 2 characters locale name, such as shown below:

![](https://i.imgur.com/YbN5UaV.png)

In this case, `en` is short for English and `es` is short for Spanish.

## Other

There is not much to this, their routes are mostly hardcoded and we don't expect much change on those. In the directory tree shown above, `Page Name` would be the exact same name as the url, e.g. `privacy` would be `/privacy`, which shows you the Privacy Policy. Yet again, these have to be translated to several languages used by the website, so it follows the same naming schema as guides, which is naming files translations by their 2 characters locale name.

### Misc

If there is anything you don't understand, please contact your department head or a website developer to help you sort these out.
