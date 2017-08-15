# Hugo Starter (No Blog)

**A [Hugo](https://gohugo.io/) boilerplate for quickly deploying single or multiple page websites without a blog**

This is a boilerplate for using Hugo as a static site generator and Gulp + Webpack as your
asset pipeline.

It uses Sass, Autoprefixer, Browser-sync, and Babel.

The default functionality to create a blog using Hugo has been removed to be as simple as possible to deploy a single or multiple page website.

## Usage

Be sure that you have the latest node and npm installed.

Next, clone this repository and run:

```bash
npm start
```

Then visit http://localhost:3000/ - BrowserSync will automatically reload CSS or
refresh the page when stylesheets or content changes.

To build your static output to the `/dist` folder, use:

```bash
npm run build
```

## Structure

```
|--site                // Everything in here will be built with hugo
|  |--archetypes       // Default frontmatter for created pages
|  |  |--default.md    // Default frontmatter for created pages
|  |--content          // Pages go here
|  |--data             // YAML data files with any data for use in examples
|  |--layouts          // This is where all templates go
|  |  |--partials      // This is where includes live
|  |  |--index.html    // The index page
|  |--static           // Files in here ends up in dist/
|  |  |--img           // Image files go here
|--src                 // Files that will pass through the asset pipeline
|  |--scss             // styles.scss will compile to dist/styles.css with sass
|  |--js               // app.js will be compiled to dist/app.js with babel
|  |  |--custom        // Write your custom js in this folder
```

## Basic Concepts

You can read more about Hugo's template language in their documentation here:

https://gohugo.io/templates/overview/

The most useful page there is the one about the available functions:

https://gohugo.io/templates/functions/

For assets that are completely static and don't need to go through the asset pipeline,
use the `site/static` folder. Images, font-files, etc, all go there.

Files in the static folder ends up in the web root. So a file called `site/static/favicon.ico`
will end up being available as `/favicon.ico` and so on...

The `src/js/app.js` file is the entrypoint for webpack and will be built to `/dist/app.js`.

You can use ES6 and use both relative imports or import libraries from npm.

All SCSS file are imported through `styles.scss` and will get compiled with Sass and PostCSS
to `/dist/styles.css`.

## Creating New Pages

To create a new page, cd to the `site/` directory and run the following command

```bash
hugo new nameofyourpage.md
```

This will create a new document inside the content folder named `nameofyourpage.md`. It will use the layout template `layouts/page/page-one.html` to generate the page. You will be able to navigate to `/nameofyourpage/` to view the new page in the browser.

## Environment variables

Two seperate the development and production *- aka build -* stages, all gulp
tasks run with a node environment variable named either `development` or 
`production`.

You can access the environment variable inside the theme files with 
`getenv "NODE_ENV"`. See the following example for a conditional statement:

    {{ if eq (getenv "NODE_ENV") "development" }}You're in development!{{ end }}

All tasks starting with *build* set the environment variable to `production` - 
the other will set it to `development`.

## Deploying to netlify

- Push your clone to your own GitHub repository.
- [Create a new site on Netlify](https://app.netlify.com/start) and link the repository.

Now netlify will build and deploy your site whenever you push to git.

You can also click this button:

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/eliwilliamson/victor-hugo)



## Enjoy!!
