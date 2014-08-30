---
layout: page
title: Configuration
---

This page lists the configuration options that you can use to customise Gorilla.

### Command-line options

You can pass configuration options to Gorilla on the Leiningen command line, for example `lein gorilla :port 8999`
would change the port the web-app runs on to 8999. Supported options are:

- `:port` : the port that the web-app runs on. Defaults to an auto-selected free port.
- `:ip` : the IP address to bind to. Defaults to `127.0.0.1`, which will allow only local access. To allow other
  computers (that you trust!) on the network access to Gorilla, bind this to a public IP address, or `0.0.0.0` to
  bind to all addresses.
- `:nrepl-port` : the port that the nREPL server will be started up on. Defaults to a free port.
 

### Configuration map options

You can also pass in options in a Leiningen profile. Gorilla will look for a `:gorilla-options` key under the user
profile. You can add options either in your `~/.lein/profiles.clj` file, or in the project's `project.clj` as
appropriate. Your `profiles.clj` file could look like:

```clojure
{:user
 {:gorilla-options
  {:keymap {"command:worksheet:newBelow" "ctrl+b ctrl+t"
            "command:worksheet:newAbove" "ctrl+b ctrl+q"}
   :load-scan-exclude #{".git" ".svn"}}}}
```

The supported options are:

- `:keymap` : a hash-map mapping Gorilla command names (see
[js/commandProcessor.js](https://github.com/JonyEpsilon/gorilla-repl/blob/develop/resources/public/js/commandProcessor.js)
 for possible values) to a keyboard
shortcut in Mousetrap format (see the [Mousetrap website](http://craig.is/killing/mice)). These values will override
the Gorilla defaults.

- `:load-scan-exclude` : a set of directory names to exclude from the scan for worksheets that is performed
whenever the load command is executed. By default `.git` directories are excluded.