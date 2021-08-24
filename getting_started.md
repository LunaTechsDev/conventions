# Getting Started

This is to help you get started with creating a brand new plugin project with LunaTea and Haxe manually without using an example project or any tools to get quickly started.

### Example Projects
If you would rather use an example project to get started then use one of the following depending on the engine you're using.

- RPG Maker
Use [LunarBase](https://github.com/LunaTechsDev/LunarBase) to quickly get started with this RPG Maker example project

- Paper Maker
Use [Origami Devtools](https://github.com/LunaTechsDev/origami-devtools) to quickly get started with this Paper Maker example project

## Prerequisites

- Install [NodeJS](ttps://nodejs.org/en/)
- Install [Haxe](https://haxe.org/)
- Install [Haxe Extension Pack for VSCode](https://marketplace.visualstudio.com/items?itemName=vshaxe.haxe-extension-pack)

## Project Setup

1. Run `npm init` to create a package.json

2. Install necessary node packages

```
npm install --save lix @lunatechs/lunatea-napkin
```

3. Create a local scope with lix (unless you want to continue installing libraries globally)

```
lix scope create
```

4. Install necessary Haxe libraries using lix

```
lix install gh:LunaTechsDev/LunaTea
```

5. Create a `compile.hxml` arguments list file for the haxe compiler in root of directory

```
# Include library
-lib LunaTea

# Copy the src directory
-cp src

# JS Version 
-D js-es=6

# Enable/Disable console.log -- tracing with the below line
--no-traces

-dce full

# Static Code Analysis For Removing  Unnecessary Code
-D analyzer-optimize 

--macro macros.MacroTools.includeJsLib("./src/Parameters.js")

-main Main

-js dist/plugin_name.js
```

6. Open your `package.json` and add a build script, for example

```json
{
  "name": "haxe-lunatea-example",
  "version": "1.0.0",
  "description": "A lunatea plugin example project",
  "dependencies": {
    "@lunatechs/lunatea-napkin": "^1.5.1",
    "lix": "^15.10.1"
  },
  "devDependencies": {},
  "scripts": {
    "build": "lix compile.hxml && napkin ./dist/"
  }
}
```
Where `napkin ./dist/` is pointing to the directory your plugin is compiled to

7. Create your `src` directory and add your `Main.hx` file and start developing

# Extras

Add a `checkstyle.json` and `hxformat.json` for style checking and auto formatting rules

See following links for examples of style and formatting rules
https://github.com/LunaTechsDev/LunarBase/blob/master/hxformat.json
https://github.com/LunaTechsDev/LunarBase/blob/master/checkstyle.json

