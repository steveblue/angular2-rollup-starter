##4.0.1

- Added more configuration to `paths.config.js
- Upgraded to Angular 4.0.1
- Added new `lib` build for distributing libraries in ES6 and ES5
- Refactored build process to default to `build` folder, `dist` is now the default for library files
- Use `npm run build:dev` instead of `npm start`
- Added `npm run build:prod` for AOT production builds
- Added `npm run build:lib` for building library files
- To stop `watcher` set `watch=false` as optional argument in any build
- Updated README


To Upgrade `paths.config.js`:

1. Move the `dep` Array to `dep.lib` and `src` to `dep.src`, `dist` to `dep.dist`.

BEFORE:

```
module.exports = {
    dep: [
            'core-js',
            'reflect-metadata',
            'zone.js',
            'systemjs',
            '@angular',
            'rxjs'
        ]
    },
    src: './node_modules',
    dist: './dist/lib',
    clean:{
      files:[],
      folders:[]
    }
}
```

AFTER:

```
module.exports = {
    dep: {
        lib: [
            'core-js',
            'reflect-metadata',
            'zone.js',
            'systemjs',
            '@angular',
            'rxjs'
        ],
        src: './node_modules',
        dist: './dist/lib'
    },
    clean:{
      files:[],
      folders:[]
    }
}
```

2. Add the project `src`, `build`, and `dist` (optional) directories. These properties point to the source directory, the folder the project should be built in, and in the case of a distributing a library, the `dist` that will be used by other projects.

```
module.exports = {
    dep: {
        lib: [
            'core-js',
            'reflect-metadata',
            'zone.js',
            'systemjs',
            '@angular',
            'rxjs'
        ],
        src: './node_modules',
        dist: './dist/lib'
    },
    clean:{
      files:[],
      folders:[]
    },
    src: 'src',
    build: 'build',
    dist: 'dist'
}

