# Pixi Inspector

A extension to the Chrome DevTools for inspecting Pixi.js games/applications.

## Installation

- download crx: https://github.com/csomakk/pixi-inspector/raw/master/release/pixiinspector.crx
- Open url: chrome://extensions
- Enable developer mode (if you haven't already)
- Drag the installer to the page to install. (You might need to drag it from Finder, not from Chrome)

## Features

* Shows the scene graph
* View and edit the properties of the selected node
* Highlight (the bounds of) the selected node
* The selected node is available in the Console as `$pixi`

## Build from source
 
* git clone git@github.com:bfanger/pixi-inspector.git
* cd pixi-inspector
* npm install
* npm install -g gulp
* npm run build
* Go to [chrome://extensions/](chrome://extensions/), click `load unpacked extension...` and browse to the build folder. 
 
### Development

Run `gulp webpack-dev-server` and open http://localhost:8090/webpack-dev-server/tests/ (or http://localhost:8090/tests/)

This loads the pixi-inspector into the same page as an example PIXI scene, which makes debugging easier. 
However in the chrome-extension environment, you don't have direct access to the PIXI object or console.log (pixi.inspector.js in an exception)
Use the [proxy](services/proxy.js) service to interact with the inspected page. 

When the inspector works in the test environment run:  
`gulp continuous-build`
Set `var DEBUG = true;` in [PixiPanel](components/PixiPanel.js) which adds a button to load the changed code.
