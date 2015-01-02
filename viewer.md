---
layout: page
title: Online viewer
---

It's really easy to share your Gorilla REPL worksheets with the world using the online viewer. It free to use, and you
don't need to register. Just upload your worksheet to GitHub and then use the link:

```
http://viewer.gorilla-repl.org/view.html?source=github&user=<>&repo=<>&path=<>
```

replacing the <>s with appropriate values. The path variable is the path inside the repo to the worksheet.
That's it - your worksheet is now available online!
[This link](http://viewer.gorilla-repl.org/view.html?source=github&user=JonyEpsilon&repo=gorilla-test&path=ws/graph-examples.clj)
is an example of a shared Gorilla worksheet.

You can also share worksheets in GitHub gists. In this case just use the link:

```
http://viewer.gorilla-repl.org/view.html?source=gist&id=<>&filename=<>
```

If the gist only has a single file in it, then you can omit the filename parameter.
[Example](http://viewer.gorilla-repl.org/view.html?source=gist&id=5baef8ac0f42706e4940)


## Limitations

- You can only access 60 worksheets per hour, coming from GitHub's API limits.
- Worksheets must be under 1MB, again a GitHub API limitation.

## Some tips for sharing worksheets

Taking care of a couple of details will make it easier for others to run your worksheets:

- It's preferable to share worksheets inside projects, rather than on their own as gists, unless they really don't have
any dependencies. This way, someone can easily clone your project and run your worksheet.
- When you share a project, make sure it's got a plugin dependency on `lein-gorilla` (it might not if you have installed
Gorilla globally in your `profiles.clj` file). If you do this then someone who clones your project to run your worksheet
will be able to simply run `lein gorilla` from the project directory and have it work.

Of course, you don't need to follow those tips. But it's definitely good to make it as easy as possible for people to
not just view your worksheets, but to copy them and run them themselves. The more the merrier you know!
