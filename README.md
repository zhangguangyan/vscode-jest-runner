# vscode-jest-runner

## Visual Studio Code Marketplace

[Go to Marketplace](https://marketplace.visualstudio.com/items?itemName=firsttris.vscode-jest-runner)

## Comparison with [vscode-jest](https://github.com/jest-community/vscode-jest)

[vscode-jest-runner](https://github.com/firsttris/vscode-jest-runner) is about running or debugging a sepcific test or test-suite, while [vscode-jest](https://github.com/jest-community/vscode-jest) is about running your current test-suite everytime you change it and it's not possible to run or debug a specific test.

## Features

Simple way to run or debug a specific test
*As it is possible in IntelliJ / Webstorm*

Run & Debug your Jest Tests from
- Context-Menu
- CodeLens
- Command Palette (strg+shift+p)

supports yarn & vscode workspaces (monorepo)
supports yarn 2 pnp
supports CRA & react-scripts! (currently only Run)

![Extension Example](https://github.com/firsttris/vscode-jest/raw/master/public/vscode-jest.gif)

## Usage with CRA or react-scripts

add the following command to settings, to pass commandline arguments
```
"jestrunner.jestCommand": "npm run test --"
```

## Extension Settings

Jest Runner will work out of the box, with a valid Jest config.   
If you have a custom setup use the following options to configure Jest Runner:

| Command | Description |
| --- | --- |
| jestrunner.configPath | Jest config path (relative to ${workFolder} e.g. jest-config.json) |
| jestrunner.jestPath | Absolute path to jest bin file (e.g. /usr/lib/node_modules/jest/bin/jest.js) |
| jestrunner.debugOptions | Add or overwrite vscode debug configurations (only in debug mode) (e.g. `"jestrunner.debugOptions": { "args": ["--no-cache"] }`) |
| jestrunner.runOptions | Add CLI Options to the Jest Command (e.g. `"jestrunner.runOptions": ["--coverage", "--colors"]`) https://jestjs.io/docs/en/cli |
| jestrunner.jestCommand | Define an alternative Jest command (e.g. for Create React App and similar abstractions) |
| jestrunner.disableCodeLens | Disable CodeLens feature |
| jestrunner.codeLensSelector | CodeLens will be shown on files matching this pattern (default **/*.{test,spec}.{js,jsx,ts,tsx}) |
| jestrunner.enableYarnPnpSupport | Enable if you are using Yarn 2 with Plug'n'Play |
| jestrunner.detectYarnPnpJestBin | Auto-detect path on Linux/Unix systems to Jest bin (Yarn 2 Pnp) |
| jestrunner.projectPath | Absolute path to project directory (e.g. /home/me/project/sub-folder) |


## Shortcuts

click File -> Preferences -> Keyboard Shortcuts -> "{}" (top right)
the json config file will open
add this:

```javascript
{
  "key": "alt+1",
  "command": "extension.runJest"
},
{
  "key": "alt+2",
  "command": "extension.debugJest"
},
```

## Want to start contributing features?

[Some open topics get you started](https://github.com/firsttris/vscode-jest-runner/issues)

## Steps to run in development mode

- npm install
- Go to Menu "Run" => "Start Debugging"

Another vscode instance will open with the just compiled extension installed.

## Notes from contributors

- By default **Jest** finds its config from the `"jest"` attribute in your `package.json` or if you export an object `module.export = {}` in a `jest.config.js` file in your project root directory.   
Read More: [Configuring Jest Docs](https://jestjs.io/docs/en/configuration)

- If Breakspoints are not working properly, try adding this to vscode config:

```javascript
"jestrunner.debugOptions": {
    "args": ["--no-cache"],
    "sourcemaps": "inline",
    "disableOptimisticBPs": true,
}
```
