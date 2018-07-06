# Udacity Feed Reader project


## Table of Contents
* [Pre requisites](#Pre requisites)
* [Building the Project](#Building the project)
* [Additional Dependencies](#Additional Dependencies)
* [Config Gulp](#Config Gulp)
* [Running the build](#Running the build)

## Pre requisites

In order to run this project we need the following installed: Node.js, NPM and Gulp.

## Building the project

To build the project, do the following steps:

Make sure you have [Node.js](https://nodejs.org/en/) installed and [NPM](https://www.npmjs.com/get-npm) .

If NPM is not installed, run the following command in console: 

```
$ npm install npm@latest -g
```

Initialize the project from the root folder by running the following commands:

```
$ npm init
```
Follow the steps to create `package.json` file.

If [Gulp.js](https://github.com/gulpjs/gulp/blob/v3.9.1/docs/getting-started.md) is not installed, install it by running the following command:

```
$ npm install --global gulp-cli
```
## Additional Dependencies

 Install additional packages in your devDependencies:

* [Gulp](https://www.npmjs.com/package/gulp)
* [Browsersync](https://www.npmjs.com/package/browser-sync) 

```
$ npm --install gulp browser-sync --save-dev
```


Install globally the [Eslint](https://www.npmjs.com/package/eslint) linter:


```
$ npm install -g eslint
```


Next run:

```
$ eslint --init
```

Creates `eslintrc.json` file, which contains the configuration for the loaded project.

## Config Gulp

In command line run:

```
$ touch gulpfile.js
```

Open the `gulpfile.js` in your IDE.

Require the Gulp and Browsersync packages.

```
var gulp = require('gulp');
var browsersync = require('browser-sync').create();
```

Set default task to watch the js files in the `src` directory:

```
gulp.task('default', () => {
	// Reloads browser
	gulp.watch('./src/**/*.js').on('change', browsersync.reload);
});
```

Create a server for Browsersync, inside the `default` task:

```
gulp.task('default', () => {
	// Reloads browser
	gulp.watch('./src/**/*.js').on('change', browsersync.reload);

	// Server
	browsersync.init({
		server: './src', // browsersync will serve files in this directory
		port: 3000,
		index: 'index.html',
		ui: false
	});
});
```

Create the `dist` task, to move all non build files to the `dist` folder:

```
gulp.task('dist', function() {
	gulp.src('./src/**/*');
	gulp.src('./*.md')
		.pipe(gulp.dest('./dist'));
});
```

## Running the build

* run the `default` task:

```
$ gulp
```

* Run the `dist` task, move non build files to the `dist` directory:

```
$ gulp dist
```
