---
layout: post
title:  "Getting started"
date:   2024-04-02 00:00:00 +1100
categories: tools
---

In our sequel journey we will be using [DuckDB](https://duckdb.org) to play with the examples.
It is a free, fast and easy-to-install tool to immediately get your own sandbox environment.

### Online
The easiest way is to navigate to a [browser version](https://shell.duckdb.org):
![DuckDB launched in web](/assets/2024-04-02-duckdb-web-shell.png)

### Locally
Alternatively, you can follow the [installation guide](http://duckdb.org/docs/installation/?version=stable&environment=cli&platform=macos&download_method=package_manager) from their official site.
If you want to store your data locally, I recommend the latter option.

Here is how you can do it on Mac:

- Install [Homebrew](https://brew.sh) (package manager)
- Run in Terminal `brew install duckdb` to install DuckDB CLI (command-line interface tool)
- Run in Terminal `duckdb` 

If you are getting similar view, then everything worked:

![DuckDB launched in CLI](/assets/2024-04-02-duckdb-cli-start.png)


