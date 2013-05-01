# OpenSeadragon Site-Build

This project compiles static web pages which provide the examples and documentation for using OpenSeadragon.

## On the Web

http://openseadragon.github.io/

## First Time Setup

All command-line operations are scripted using [Grunt](http://gruntjs.com/) which is based on [Node.js](http://nodejs.org/). To get set up:

1. Install Node, if you haven't already (available at the link above)
1. Install the Grunt command line runner (if you haven't already); on the command line, run `npm install -g grunt-cli`
1. Clone the site-build repository
1. On the command line, go in to the site-build folder
1. Run `npm install`

You're set... continue reading for build and test instructions.

## Building the Web Pages

To build, just run (on the command line, in the site-build folder):

    grunt build

The built website will appear in site-build/build.

If you want to try the site out in your browser, you can run:
    
    grunt connect watch

This will run a server at http://localhost:9000/.

## Building the Docs

    grunt doc

... will build the docs into the local build folder.

## Publishing

To publish, run:

    grunt publish

This cleans out the openseadragon.github.com folder (which you've cloned from the openseadragon.github.com repository, and resides next to your site-build folder) and builds and copies the web pages and docs into it.

Note that while the OpenSeadragon website resides at http://openseadragon.github.io, for historical reasons the repository is named openseadragon.github.com.

## Example Images

If you want to see the website with the appropriate example images, clone the example-images repository into site-build/build and check out its gh-pages branch.

## New JSDoc

This branch is to work on the new JSDoc integration. Don't forget to `npm install`. You'll also need Java and to have your JAVA_HOME set up. For the latter, if you're on Mac, you can add `export JAVA_HOME=/System/Library/Frameworks/JavaVM.framework/Versions/CurrentJDK/Home` to your Bash profile.

Issues:

* The new version of http://openseadragon.github.io/docs/symbols/OpenSeadragon.html doesn't show any of the methods or properties. The other classes seem fine (though I haven't checked them all). 
* It says things like `new Point()` instead of `new OpenSeadragon.Point()`; misleading.
* We have a couple of private functions with examples of file formats in the doc comment... the new JSDoc chokes on them. Since they're private, it's easy enough to move them to just normal comments instead. I've done that in this branch, but we want to make the change upstream in the openseadragon/openseadragon repo.
* The new version of http://openseadragon.github.io/docs/symbols/src/built-openseadragon_openseadragon_openseadragon.js.html chokes (at least in Firefox Mac) during syntax highlighting, whereas the old one does not.

Once everything is sorted out and we're ready to merge, we should remove the build.xml and build.properties files, and the jsdoc folder. I've left them there for now for reference. Also this section of the readme should then get re-integrated into the Docs section above as needed.
