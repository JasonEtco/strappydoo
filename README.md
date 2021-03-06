![strappydoo](https://user-images.githubusercontent.com/10660468/37246132-814011d0-2471-11e8-9d02-81d7085565af.png)

> a command line tool that provides bootstrap scripts to run all projects

Easily switch between projects that are written in different languages without having to remember how each language handles common tasks like installing dependencies, starting a server, and running the tests.

This project is an abstraction of the [Scripts to Rule Them All](https://githubengineering.com/scripts-to-rule-them-all/) pattern that is common at GitHub.

## Installation

```
$ git clone https://github.com/bkeepers/strappydoo.git ~/.strappydoo
$ ~/.strappydoo/script/install
```

### Usage

- `strappy bootstrap` - Bootstrap dependencies
- `strappy console` - Start an interactive console
- `strappy server` - Start the server
- `strappy test` - Run the tests

### Supported languages & frameworks

- [x] NPM
- [x] Homebrew
- [x] Rails
- [x] Bundler
- [x] script/*
- [ ] Ruby (Gemfile, Rack, minitest, etc)
- [ ] Python (Django, …)
- [ ] ???

Want to add support for another language or framework? Just [create a file in `plugins/`](https://github.com/bkeepers/strappydoo/new/master/plugins). Here's an example for a fictional framework called `scrappy`, defined in `plugins/scrappy.sh`:

```sh
#!/bin/sh

# Test if Scrappyfile exists or return 1 to disable this plugin
test -f Scrappyfile || return 1

# Now define a function called `{framework}_${command}` that runs the relevant command for each of:
#
# - bootstrap
# - server
# - console
# - test

scrappy_bootstrap() {
  scrappy install
}
scrappy_server() {
  scrappy run
}
scrappy_console() {
  scrappy term
}
scrappy_test() {
  scrappy test
}
```

### TODO

- [ ] tests
- [ ] allow sourcing aliases in shell startup scripts (e.g. `source $(strappy aliases)`)
- [ ] Add support for other common languages/frameworks
- [ ] Make it easy to register custom plugins
- [ ] Distribute via homebrew
