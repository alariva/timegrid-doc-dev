# Assets

Assets are managed with [Bower](http://bower.io/).

The `gulpfile.js` groups assets by their possible simultaneous usage.

For example, most input jQuery/Bootstrap plugins are grouped together into the `forms.js` and `forms.css` files.

This makes sure all enhanced input facilities are available when this is required, by just including these two asset files.

More information about publishing the assets to `public/` [can be found here](http://laravelcoding.com/blog/laravel-5-beauty-using-bower).

# Installed Components

The current installed components can be found in the `bower.json` file.
