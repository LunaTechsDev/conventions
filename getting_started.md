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

- **For RPG Maker:**
```
npm install --save lix @lunatechs/lunatea-napkin
```

- **For Paper Maker:**
- 
```
npm install --save lix @lunatechs/lunatea-napkin prettier
```

1. Create a local scope with lix (unless you want to continue installing libraries globally)

```
lix scope create
```

4. Install necessary Haxe libraries using lix


- **For RPG Maker:**
```
lix install gh:LunaTechsDev/LunaTea
```

- **For Paper Maker**

```
lix install gh:LunaTechsDev/PaperTea
```

1. Create a `compile.hxml` arguments list file for the haxe compiler in root of directory

- **For RPG Maker:**
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

- **For Paper Maker:**

```
-lib PaperTea

-cp src

--macro core.Macros.setOutput()
--macro core.Macros.copyDetails()

--dce full

-D js-es=6
-D js-classic

-main Main

--each
--next
# Filled out via a macro
--js game\

--next
-D dist
# Filled out via a macro
--js dist\

--macro core.Macros.runNapkin()
```

1. Open your `package.json` and add a build script, for example

- **For RPG Maker:**
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

- **For Paper Maker:**
  
```json
{
  "devDependencies": {
    "@lunatechs/lunatea-napkin": "2.0.1",
    "lix": "^15.10.1",
    "prettier": "^2.3.2"
  },
  "scripts": {
    "build": "lix compile.hxml",
  }
}
```

1. Create your `src` directory and add your `Main.hx` file and start developing

# Extras

Add a `checkstyle.json` and `hxformat.json` for style checking and auto formatting rules

See following links for examples of style and formatting rules
https://github.com/LunaTechsDev/LunarBase/blob/master/hxformat.json
https://github.com/LunaTechsDev/LunarBase/blob/master/checkstyle.json

