# Portfolio: editing your projects

This site is a single file, `index.html`. It needs no build step and nothing to install. All of your project content sits in one list near the bottom of that file, so updating the site means editing that list and saving.

## Contents

- [Files](#files)
- [Preview your changes](#preview-your-changes)
- [Where the projects are](#where-the-projects-are)
- [Edit an existing project](#edit-an-existing-project)
- [Add a new project](#add-a-new-project)
- [Remove a project](#remove-a-project)
- [Change the order](#change-the-order)
- [Add or replace images](#add-or-replace-images)
- [Field reference](#field-reference)
- [Common mistakes](#common-mistakes)

## Files

```
portfolio-web/
├── index.html          ← the whole site, including your project list
├── README.md           ← this guide
└── images/
    ├── tern/           ← one folder per project, named after its id
    │   ├── 1.svg
    │   ├── 2.svg
    │   └── 3.svg
    ├── library/
    ├── buses/
    ├── shelf/
    └── specimen/
```

The images in these folders are samples. Replace them with your own screenshots and photos.

## Preview your changes

1. Save `index.html`.
2. Double-click it to open it in your browser. If it's already open, refresh the page.

To stop images going missing, keep `index.html` and the `images` folder side by side, as shown above.

## Where the projects are

Open `index.html` and search for:

```
const PROJECTS = [
```

Everything from that line to the closing `];` is your project list. Each project is one block wrapped in `{ ... }`, and a comma separates each block from the next. Don't edit anything below the line that says `Rendering (no need to edit below)`.

## Edit an existing project

Find the project's block and change the text between the quotation marks. For example, to change a title:

```js
title: "Tern: a tiny language that compiles to WebAssembly",
```

becomes

```js
title: "Tern: a teaching language for the web",
```

Save and refresh to see the change.

## Add a new project

1. **Copy this template.**

   ```js
   {
     id: "my-project",
     code: "CS 1234", term: "Fall 2026", area: "Software",
     title: "Project title",
     summary: "One sentence about what it is.",
     tags: ["Tool one", "Tool two", "Topic"],
     color: "#2F6B4F",
     images: [
       { src: "images/my-project/1.jpg", caption: "What this image shows." },
       { src: "images/my-project/2.jpg", caption: "What this image shows." }
     ],
     sections: [
       { heading: "The brief", body: "What the assignment asked for." },
       { heading: "What I built", body: "What you made and how." },
       { heading: "What I learned", body: "What you would do differently, or what surprised you." }
     ],
     facts: {
       Role: "Solo project",
       Duration: "6 weeks",
       Tools: "Python, Figma",
       Links: [["Source on GitHub", "https://github.com/you/repo"], ["Live demo", "https://example.com"]]
     }
   },
   ```

2. **Paste it into the list.** Put it right after `const PROJECTS = [` to show it first, or anywhere between two existing projects. Make sure the block ends with `},` and that the project before it also ends with `},`.

3. **Pick a unique `id`.** Use lower case with no spaces, such as `weather-app`.

4. **Make an image folder** with the same name as the `id`: `images/weather-app/`. Then add your images to it (see [Add or replace images](#add-or-replace-images)).

5. **Fill in the rest of the fields.** The [field reference](#field-reference) explains each one.

6. **Save and refresh.**

## Remove a project

1. Delete the project's whole block, from its opening `{` to its closing `},`.
2. If you want, delete its folder in `images/` too.
3. Save and refresh.

## Change the order

Projects appear on the page in the same order as in the list. To move one, cut its whole block (from `{` to `},`) and paste it in the new position.

## Add or replace images

1. **Prepare the file.** JPG, PNG, WebP and SVG all work. Landscape images with a width-to-height ratio of about 8:5 fit best, for example 1600 × 1000 pixels. Keep each file under about 500 KB so the page loads quickly.
2. **Put it in the project's folder,** for example `images/tern/playground.jpg`.
3. **Point to it in the project's `images` list:**

   ```js
   images: [
     { src: "images/tern/playground.jpg", caption: "The online playground." },
     { src: "images/tern/errors.png", caption: "Type errors point at the exact expression." }
   ],
   ```

The first image in the list is also the thumbnail shown in the project list on the main page. Put your strongest image first.

You can give a project as many images as you like. When a project has more than one, small preview buttons appear under the main image so visitors can switch between them.

If you leave `src` empty (`src: ""`), the site shows a coloured placeholder in its place. This is handy while you're still gathering images.

**Paths are case-sensitive once the site is online.** `images/Tern/1.JPG` and `images/tern/1.jpg` count as different files. Using lower case everywhere avoids the problem.

## Field reference

| Field | What it's for | Example |
|---|---|---|
| `id` | A unique short name. The site uses it internally, and it should match the project's image folder name. Lower case, no spaces. | `"tern"` |
| `code` | The course code, shown in bold next to the project. | `"CS 4120"` |
| `term` | When you took the course, shown under the course code. | `"Spring 2026"` |
| `area` | A category label. The page doesn't show it at the moment, so you can use any value. | `"Software"` |
| `title` | The project name, shown as the clickable heading. | `"Where the buses run late"` |
| `summary` | One sentence under the title. It also appears at the top of the project's detail view. | `"An interactive map of…"` |
| `tags` | A short list of tools or topics, shown under the summary. | `["Python", "D3.js"]` |
| `color` | The background colour of the placeholder image, as a hex code. It's only used when an image's `src` is empty. | `"#3D5A80"` |
| `images` | The pictures for the project. Each one has a `src` (the file path) and a `caption` (the text shown under it). | see above |
| `sections` | The write-up in the detail view. Each section has a `heading` and a `body`. Add or remove as many as you like. | `{ heading: "The brief", body: "…" }` |
| `facts` | The side panel of key facts in the detail view. Each label on the left becomes a row. Use any labels you like, such as `Role`, `Grade`, `Team` or `Users`. | `Role: "Solo project"` |
| `facts.Links` | Optional. A list of links, each written as `["Link text", "address"]`. | `[["Source on GitHub", "https://…"]]` |

## Common mistakes

If the project list goes blank after an edit, one of these is usually the cause:

- **A missing comma** between two projects (`}` followed by `{` without `},` in between), or between two fields.
- **A missing or extra quotation mark,** for example `title: "My project,` with no closing quote.
- **A `"` inside your text.** Use a single quote instead, or put a backslash before it:
  `summary: "A \"tiny\" language"`.
- **Unbalanced brackets.** Every `{` needs a matching `}`, and every `[` needs a matching `]`.
- **Two projects with the same `id`.** Clicking one of them will open the other.

To find the exact line, open the page in your browser, right-click, choose **Inspect**, and open the **Console** tab. The error message there includes a line number.

If you're stuck, undo your last change (Ctrl+Z, or Cmd+Z on a Mac), save, and refresh. Then try the edit again one step at a time.
