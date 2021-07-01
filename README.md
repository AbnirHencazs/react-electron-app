# Electron application using React via Webpack
This is an application starting point to show how to run an electron application using react.

This was possible due to [electron webpack template](https://www.electronforge.io/templates/webpack-template), which offered a base for then adding react and babel dependencies.

## Babel configuration
To set up babel to transpile the react code to browser-friendly one, we have to edit the `webpack.rules.js` file with the following

```sh
module.exports = [
  // ... existing loader config ...
  {
    test: /\.jsx?$/,
    use: {
      loader: 'babel-loader',
      options: {
        exclude: /node_modules/,
        presets: ['@babel/preset-react']
      }
    }
  },
  // ... existing loader config ...
]
```

## Actually implementing react application on top of electron
So as specified in [electron's process model](https://www.electronjs.org/docs/tutorial/process-model) renderers have their own isolated context, fortunately there is a way of _injecting_ code to the main process via preLoading scripts, which is the function of the renderer file from which we will import the actual react application.

## Running the application
In order to start the application run the following npm script

```sh
npm start
```