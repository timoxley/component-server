# Component Server

Serve custom [components](https://github.com/component/component/wiki/Components) from your local machine.

This module is mainly for development purposes, and will become less useful once
`component(1)` [supports lookup paths](https://github.com/component/component/issues/30). 

Component Server is similar to [component/server](https://github.com/component/server/) but
removes the need to nest components under a namespace directory or master 'branch'
directory.

## Installation

    $ npm install -g component-server

## Instructions

Create a component in components.local:

		$ mkdir component.local
		$ cd component.local
		$ component create my-component  

Add local component server to your `component.json` remotes, and depend
on your component using the `local` namespace.

```json
{
	...
  "remotes": ["http://localhost:3939"],
  "dependencies": {
    "local/my-component": "*"
  }
	...
}
```

Run component-server in your project directory:

		$ component-server
		serving components from components.local on port 3939


Run component installation fro your project (in a new terminal)

		$ component install

     install : local/my-component@master
       fetch : local/my-component:index.js
    complete : local/my-component

Your local component is now installed and ready to be built!

## Usage
From `component-server --help`

```
Usage: component-server [options]

Options:

	-h, --help                   output usage information
	-V, --version                output the version number
	-p, --port <port>            specify the port [3939]
	-d, --dir <directory>        specify the component dir relative to cwd [components.local]
	-n, --namespace <namespace>  serve local components under this namespace [local]
	-v, --verbose                output component server connection logs
```
