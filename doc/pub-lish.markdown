---
title: "Command: Publish"
---

    $ pub publish

This command publishes your package on
[pub.dartlang.org](http://pub.dartlang.org) for anyone to download and depend
on. For example, if your package is named transmogrify, it will be listed on
`http://pub.dartlang.org/packages/transmogify`, and users can depend on it in
their pubspecs and get it via [pub install](pub-install.html) using something
like:

{% highlight dart %}
dependencies:
  transmogrify: ">= 1.0.0 < 2.0.0"
{% endhighlight %}

When publishing a package, it's important to follow the [pubspec
format](pubspec.html) and [package layout conventions](package-layout.html).
Some of these are required in order for others to be able to use your package.
Others are suggestions to help make it easier for users to understand and work
with your package. In both cases, pub will try to help you by pointing out what
changes will help make your package play nicer with the Dart ecosystem.
There are a couple of additional requirements for uploading a package:

* You must include a license file (named `LICENSE`, `COPYING`, or some
  variation) that contains an [open-source license](http://opensource.org/). We
  recommend the [BSD license](http://opensource.org/licenses/BSD-2-Clause),
  which is used by Dart itself. You must also have the legal right to
  redistribute anything that you upload as part of your package.

* Your package must be less than ten megabytes large after gzip compression. If
  it's too large, consider splitting it into multiple packages, or cutting down
  on the number of included resources or examples.

Be aware that the email address associated with your Google account will be
displayed on [pub.dartlang.org](http://pub.dartlang.org) along with any packages
you upload.

## What files are published?

**All files** in your package will be included in the published package, with
the following exceptions:

* Any `packages` directories.
* Your package's [lockfile](glossary.html#lockfile).
* If you're using Git, any files ignored by your `.gitignore` file.
* If you aren't using Git, all "hidden" files (that is, files whose names begin
  with `.`).

If there are other files you don't want to include, be sure to delete them (or
add them to `.gitignore`) before running `pub publish`.

To be on the safe side, `pub publish` will list all files it's going to publish
for you to look over before it actually uploads your package.

## Deleting a published package

Once a package is published, you're strongly discouraged from deleting it. After
all, some user could already be depending on it! If you accidentally included
your password or something similarly secret in the package, [file an
issue][delete-request] and the Pub authors will take down your package. You'll
need to use a different version when you re-upload it, though.

[delete-request]: http://code.google.com/p/dart/issues/entry?summary=Request%20to%20delete%20package%20from%20pub&status=Triaged&labels=Type-Task,Priority-Medium,Area-Pub,Pub-DeleteRequest
