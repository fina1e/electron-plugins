# electron-plugins fork
Plugin loader for electron applications.

## Installation
download electron-plugins and save it to the project

## Usage for the main application:
In your electron render process you can load your plugins like so:
```
var plugins = require('electron-plugins');
```
```
document.addEventListener('DOMContentLoaded', function () {
  var context = { document: document };
  plugins.load(pluginname, context, function (err, loaded) {
  if(err) return console.error(err);
     console.log('Plugins loaded successfully.');
    });
```

create into the html file a div space for each plugin with id = pluginnamepluginname.
also a extra file "plugin.json" is needed, where the specific plugins are declared.

## Usage for the plugin:
Your plugin should export a constructor function, which is passed the context object upon instantiation. You can put whatever you want onto the context object.
the id is made up of the pluginame, written two times together. 
```
function Plugin(context, id) {
	context.document.getElementById(id).innerHTML= '<br><br>new Plugin content from plug2!';
}
module.exports = Plugin
```

## Examples
* [electron-updater-sample](https://github.com/EvolveLabs/electron-updater-sample)
* [electron-updater-sample-plugin](https://github.com/EvolveLabs/electron-updater-sample-plugin)

## Related
* [electron-updater](https://github.com/EvolveLabs/electron-updater)
