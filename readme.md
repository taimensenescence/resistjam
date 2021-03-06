# \#ResistJam

Praise kek and whatnot.

## Installing

### Node.js and Grunt

You will need to first install [Node.js](http://nodejs.org/download/) and the grunt-cli: `npm install -g grunt-cli`.

### Setup project

Checkout from source:

    git clone git@github.com:kararty/resistjam kekistani-jam
    cd kekistani-jam

Next, inside the project, you need to install the project's various NPM dependencies:

    npm install

And you should now be ready to spin up a development build of your new project:

    grunt

## Developing

Files in `src/js/game/states/` is where the code is.

Files in the `build` directory will always be generated, as such these will removed without warning and should generally not be edited.

### Recommendations

* Use relative file paths for any assets loaded by your HTML or JavaScript. This will negate any potential path issues when the game is later uploaded to a webserver.
* If you intend to store development assets (i.e PSD's, Texture Packer files, etc) inside your project, store them outside of the `src` directory to avoid bloating your builds with them.

### Available Targets

#### `grunt`

Configures and runs an unminified development build optimised for fast watch performance with source maps and live reload.

#### `grunt build`

Creates an uglified, production ready build with no source maps.

#### `grunt optimise`

Lossy compression of all png's in the `src/images/` directory using [pngquant](http://pngquant.org/).

(Linux users will need to have a version of pngquant available on their paths.)

#### `grunt zip`

Compiles the current build into `{title}.zip` with an internal folder. This is intended for use when transferring the build to a third party for webserver upload.

#### `grunt cocoon`

Compiles the current build into `{title}.zip` ready for upload to [CocoonJs](https://www.ludei.com/cocoonjs/).

### Phaser and it's Physics Engines

You might notice that Phaser isn't actually bundled in with the rest of our Browserify bundle. Bundling it was our first choice initially, however leaving it out enables use of the P2 Physics engine and makes `grunt:browserify` run a whole lot faster. It also gives you the option to pull Phaser from in a [CDN](https://github.com/photonstorm/phaser#cdn).

#### Using P2

The project comes ready to run Phaser with arcade physics, but can easily be adjusted to use the P2 physics engine.

The [`grunt:copy` task](https://github.com/lukewilde/phaser-js-boilerplate/blob/feature/remove-phaser-from-bundle/gruntfile.js#L179-L198) contains directives which can be used in [`grunt:default`](https://github.com/lukewilde/phaser-js-boilerplate/blob/feature/remove-phaser-from-bundle/gruntfile.js#L233) and [`grunt:build`](https://github.com/lukewilde/phaser-js-boilerplate/blob/feature/remove-phaser-from-bundle/gruntfile.js#L249) to copy in your physics engine of choice.

### Updating or Adding Libraries

When adding new libraries that aren't CommonJS compatible, you'll have to update the [Browserify Shim configuration](https://github.com/thlorenz/browserify-shim#3-provide-browserify-shim-config).

### This is a clone from lukewilde's phaser-boilerplate.