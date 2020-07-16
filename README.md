# APISuite Portal UI Extension Demo

## About

This repo contains an APISuite Portal UI Extension skeleton for demonstration purposes.

## Stack

- [Rollup](https://github.com/rollup/rollup)
- [Sass](https://sass-lang.com/)
- [TypeScript](https://www.typescriptlang.org/)

## Acknowledgments

The repo is based on a stripped-down version of a React Component Library project skeleton. More info:

* [Repo](https://github.com/HarveyD/react-component-library)
* [Blog post](https://blog.harveydelaney.com/creating-your-own-react-component-library/)

It also features:

- [Jest](https://jestjs.io/) and [React Testing Library](https://github.com/testing-library/react-testing-library) enabling testing of the components

## Development

### Testing

```
npm run test
```

### Building

```
npm run build
```

or, to watch the projecto for changes and rebuilding it:

```
npm run build:watch
```

Don't forget to add the component to your `index.ts` exports if you want the library to export the component!

### Installing Component Library Locally

While developing the extension, you might want to test it in the APISuite portal. You can install it there with

```
npm i --save ../../apisuite-extension-ui-demo/dev-symlink-target
```

The reason for referencing the `dev-symlink-target` folder is because itself references only the `package.json` file and the `build` folder. It leaves the `node_modules` folder out which allows us to use the same React instance that is installed by the APISuite portal for both the portal and the extension.

### Hosting via GitHub

I recommend you host the component library using NPM. However, if you don't want to use NPM, you can use GitHub to host it instead.

You'll need to remove `build/` from `.gitignore`, build the component library (`npm run build`), add, commit and push the contents of `build`. [See this branch for an example.](https://github.com/HarveyD/react-component-library/tree/host-via-github)

You can then install your library into other projects by running:

```
npm i --save github:Cloudoki/apisuite-extension-ui-demo#branch-name
```

### Supporting Image Imports

Add the following library to your component library [@rollup/plugin-image](https://github.com/rollup/plugins/tree/master/packages/image):

```
npm i -D @rollup/plugin-image
```

Then add it to `rollup-config.js`:

```
...
plugins:[
  ...,
  image(),
  ...
]
...
```

You can then import and render images in your components like:

```tsx
import logo from "./rollup.png";

export const ImageComponent = () => (
  <div>
    <img src={logo} />
  </div>
);
```