<img src="docs\images\squido.png" width="100px" height="auto">

# squido

`squido` is a dead simple static website builder which can be hosted anywhere for super fast websites and very little effort.

```bash
# with npm
npm install -g squido

# or with Yarn
yarn global add squido
```

## Demo

A demo can be found [https://squido.netlify.app](https://squido.netlify.app)

## Structure

You can start by grabbing everything in the `/source` directory of [here](https://github.com/mrvautin/squido/tree/main/source).

```
project
│   config.js 
│
└───source
│   index.hbs
│   post.hbs
│   package.json
│   │
│   └───posts
│   │   post1.markdown
│   │   post2.markdown
│   │
│   └───layouts
│   │   layout.hbs
│   │
│   └───content
│       └───images
│       │
│       └───javascripts
│       │
│       └───stylesheets
```

The `/source` directory is required

The `index.hbs` and `post.hbs` files are used to insert into your template. The index is the root of your website and the `post.hbs` will render the contents of the `.markdown` files.

Your posts go in the `/source/posts` directory. You will have `.markdown` files for each post/page you want.

The `content` directory contains the files used for your website. Eg: Stylesheets, images, javascript files etc.

## Usage

The CLI comes with a few commands. 

``` bash
Usage: cli [options] [command]

Options:
  -V, --version    output the version number
  -h, --help       output usage information

Commands:
  build [options]  Builds your website
  clean            Clean your website build
  serve [options]  Serves website
```

#### Build command

The `build` command has the following options:

``` bash
Usage: build [options]

Builds your website

Options:
  -c --clean  Cleans build directory
  -h, --help  output usage information
```

#### Clean command

The `clean` command has the following options:

``` bash
Usage: clean [options]

Clean your website build

Options:
  -h, --help  output usage information
```

#### Serve command

The `serve` command has the following options:

``` bash
Usage: serve [options]

Serves website

Options:
  -w --watch  Watches for changes
  -b --build  Builds on start
  -c --clean  Cleans build directory
  -h, --help  output usage information
```

## Config

An example config can be seen below. You can see that you can specify different values for different environments you run. `development` and `production` are examples but they need to match up with whatever `NODE_ENV` is set. If one is not set, the default is `development`.

``` javascript
const config = {
    development: {
        name: 'squido',
        description: 'This is the blog description',
        twitterHandle: '@mrvautin',
        baseUrl: 'http://localhost:4965',
        sourcesExt: 'markdown',
        summaryLength: 250,
        port: 4965
    },
    production: {
        name: 'squido',
        description: 'This is the blog description',
        twitterHandle: '@mrvautin',
        baseUrl: 'http://example.com',
        sourcesExt: 'markdown',
        summaryLength: 250,
        port: 4965
    }
};

module.exports = config;
```

The configuration options are self explanatory. You can use any of the config in your template files using `{{meta.config.<option>}}`. Eg: For example `{{meta.config.baseUrl}}`.

This is a static website so the `port` is used for spinning up a Web Server for development. 

## Posts

Posts have a meta data component at the top of the file which directs how the file is built. The meta data is `yaml` formatted and sits between two `---` tags. Eg:

``` yaml
---
title: Caede virides oculos armentis
permalink: caede-virides-oculos-armentis
description: Caede virides oculos armentis
date: '2021-03-11 19:17:00'
---
```

You can add more but the example layouts uses the `title` and `description` for SEO for page title. 

The permalink is required. Its used to build the URL for your website: Eg. The above will output a post at: `https://example.com/caede-virides-oculos-armentis`

## Deployment / Hosting

You can host this website anywhere you can host static websites. Some options are [https://www.netlify.com](https://www.netlify.com) as the deployments are just dead simple.

<img src="docs\images\netlify.png" width="800px" height="auto">