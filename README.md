# Unofficial Minetest API documentation

This github repo contains the source files for the site and the site HTML files.

Feel free to make a pull request, not on the gh-pages branch though.

# Editing the site
To add a new page, just create a new file in the `docs/` directory and give it an appropriate name.

You are not required to install MkDocs just to edit the source files, but you will need it to preview the changes.

To preview the changes you've made to the source files, open up a terminal in the repo's main directory and run `mkdocs serve` and navigate to `localhost:8000` on your browser.

# Building the site
Before we begin, please note that this step requires MkDocs and that you are not required to build the site for a pull request.

After you're done editing the source files and feel like they're ready to be published, open up a terminal in the repo's main directory and run `mkdocs build`. In case you want to deploy the site on your own GitHub Pages, run `mkdocs gh-deploy`