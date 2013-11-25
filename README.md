va-open-data
============

The /data page for the VA. Will be visible at http://www.va.gov/data

# Notes
We copied the existing `<head>` content from va.gov, and also the existing `<body>` content up until `<div =id="hp-content-main">` (line 379 of `index.html`).

We updated image and javascript `src=` and `href=`'s to absolute paths (i.e. `http://www.va.gov/va_files/2012/styles/template_styles.css` instead of `va_files/2012/styles/template_styles.css`) so that we could test locally. For production, these should probably go back to the relative paths so we don't mess up any caching strategy currently being used to serve those assets (depending on how this gets deployed). It shouldn't break anything to leave them in, though.

We rely on a combination of existing VA.gov CSS and new CSS defined in `slash-data.css` (compiled from SASS -- see note below). All new CSS elements are namespaced within the `#slash-data` id, so there shouldn't be any conflicts with other VA CSS if you want to merge it into master. Alternately, you can include this new it as a separate stylsheet using this tag in header:

`<link href="css/main.css" media="all" rel="stylesheet" type="text/css">`

# Running Locally
The Slash-Data CSS is generated from a SASS file. It's best to edit the .scss directly rather than the generated .css

To do this, [install SASS](http://sass-lang.com/install). Then, `cd` into the va-open-data directory and run:

`$ sass --watch sass/main.scss:css/slash-data.css`

This will watch for changes in `main.scss` and updated `slash-data.css` accordingly.

The project includes [Bourbon Neat](http://neat.bourbon.io/), a CSS grid framework. All required files are included in the /sass directory and are only mixed into the `slash-data.css` when needed. 

# License
This project constitutes a work of the United States Government and is not subject to domestic copyright protection under 17 USC § 105.