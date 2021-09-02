# Proyecto Base para maquetar CSS con Sass y Gulp

#### Descripción:

Esta es una plantilla para implementar desafios para maquetar paginas web usando sass con gulp.

### Técnologia empleada

- [sass]
- [gulp]

#### _**Configuracion de paquetes:**_

```sh
$ npm install -D gulp gulp-sass gulp-minify-css gulp-concat sass
```

#### _**Configuracion de scripts:**_

```sh
	  "scripts": {
		"build:CSS": "gulp build_CSS",
		"build:minifyCSS": "gulp build_minifyCSS",
		"watch:CSS": "gulp watch_CSS"
	  },
```

#### _**Configuracion de archivo gulpfile.js:**_

```sh
	const gulp = require("gulp");
	const sass = require("gulp-sass")(require("sass"));
	const minifyCSS = require("gulp-minify-css");
	const concat = require("gulp-concat");

	gulp.task("build_CSS", () => {
	  return gulp
		.src("sass/**/*.scss")
		.pipe(sass())
		.pipe(concat("styles.css"))
		.pipe(gulp.dest("public/css"));
	});

	gulp.task("build_minifyCSS", () => {
	  return gulp
		.src("sass/**/*.scss")
		.pipe(sass())
		.pipe(minifyCSS())
		.pipe(concat("styles.min.css"))
		.pipe(gulp.dest("public/css"));
	});

	gulp.task("watch_CSS", () => {
	  gulp.watch("sass/**/*.scss", gulp.series("build_CSS"));
	});

	gulp.task("watch_minifyCSS", () => {
	  gulp.watch("scss/**/*.scss", gulp.series("build_minifyCSS"));
	});
```
