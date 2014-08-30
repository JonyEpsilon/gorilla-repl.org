---
layout: page
title: Using with other editors
---

Gorilla REPL works well with other editors and IDEs. This page has some setup hints to get Gorilla and your editor/IDE
of choice working well together.

## IntelliJ IDEA / Cursive Clojure

It's straightforward to get [Cursive](http://cursiveclojure.com) and Gorilla to share an nREPL server, so that you can
work on the worksheets and code in a project together. 

Note that Gorilla must start the nREPL server, as it needs to insert its own rendering middleware. So, the way to do it
is, first run an instance of Gorilla. And then second, use a "remote" REPL connection in Cursive to connect to the nREPL
server that Gorilla started. Gorilla will write out a `.nrepl-port` file that Cursive can use to auto-detect the port
that Gorilla started the nREPL server on.

It's convenient to run Gorilla from within IntelliJ. You can very easily do this by making a "Leiningen" run
configuration, that starts in your project's directory, to run the `gorilla` task.

**Coming soon.** You can open worksheets from within Gorilla using the "Gorilla REPL helper" IntelliJ plugin. It will
auto-detect the port of the Gorilla server running in the project.

There are a [couple of videos](/videos.html) that go through in detail setting up Leiningen, Gorilla and Cursive to
work well together.

## Emacs and CIDER

Should you prefer more of an antique editing experience, then Gorilla also works well with Emacs :-) You can connect
CIDER and Gorilla to the same nREPL server and enjoy editing your code in emacs while editing your notebooks in
Gorilla.

The only thing to note is that you must start the nREPL server by running `lein gorilla`, and then connect to
this from emacs with `cider-connect`. Gorilla will write out a `.nrepl-port` file in the standard place, so CIDER will
be able to autodetect the port. It's necessary to do it this way round because Gorilla needs to insert its own rendering
middleware in to the nREPL server. By default Gorilla will insert a recent version of the `cider-nrepl` middleware, but
you can override this with a version of your choosing by adding `cider-nrepl` to your `:plugins` vector in the usual
way (see the CIDER readme for more details).

## Vim

I am told that Gorilla works with VIM and fireplace, but haven't used it myself. If anyone wants to contribute some
notes, they'd be very welcome :-)