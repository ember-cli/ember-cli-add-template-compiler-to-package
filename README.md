# ember-cli-add-template-compiler-to-package
This is a utility to add a template compiler (ember-cli-htmlbars) to your addon's package.json. It is intended to be used inside ember-cli blueprints.

# Usage
This utility returns a promise and is meant to be used inside the afterInstall hook of a blueprint. The function expects the path to your project's root, and the name of the template compiler to add to your package.json. The primary usage for this is

```js
// A blueprint
var path = require('path');
var addPackageTemplateCompiler = require('ember-cli-add-template-compiler-to-package');

module.exports = {
  afterInstall: function(options) {
    if (options.project.isEmberCLIAddon() || options.inRepoAddon) {
      var projectRoot = options.inRepoAddon ? path.join(this.project.root, 'lib', options.inRepoAddon) : this.project.root;
      return addPackageTemplateCompiler(projectRoot);
    }
  }
}
```
