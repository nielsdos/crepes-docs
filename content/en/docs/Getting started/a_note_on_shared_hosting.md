---
tags: ["installation"]
title: "A Note on Shared Hosting"
linkTitle: "A Note on Shared Hosting"
weight: 12
description: >
  What you should beware of when using shared hosting.
---

The document root of the application is the public folder.
Do *not* place the whole application in the document root, or otherwise your risk creating security issues!
It is especially dangerous if the environment file `.env` is readable by the outside world because it contains application secrets.

The safe way to set up a Laravel application (like this application is) on shared hosting is by placing the whole application directory *outside* of the document root in a dedicated folder. For example you can name that folders `crepes`.
The files in the `public` folder should be the ones placed in the document root.

You then need to make a few modifications to `public/index.php` in order to accomodate for the changed application directory structure. In particular lines 10 and 11 need changes. The code initially looks like this:

```php {linenostart=10,linenos=table}
require __DIR__.'/../vendor/autoload.php';
$app = require_once __DIR__.'/../bootstrap/app.php';
```

If your document root is at `/public_html`, and the application code is at `/crepes`, you should change the code to:

```php {linenostart=10,linenos=table}
require __DIR__.'/../crepes/vendor/autoload.php';
$app = require_once __DIR__.'/../crepes/bootstrap/app.php';
```
