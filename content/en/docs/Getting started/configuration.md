---
tags: ["installation"]
title: "Configuration"
linkTitle: "Configuration"
weight: 20
description: >
  Configuring the application.
---

This page will guide you on how to configure the application.

## Creating an environment file (`.env`)

The configuration settings are stored within the `.env` file.
To create one you should copy the example file `.env.example` to `.env`.

> Make sure that the .env file is *never* accessible by the outside world: it contains application secrets such as your database password!

## Editing the environment file

You should modify the .env file to configure the application. This includes settings for the database, reCAPTCHA settings, and email settings. In particular, the following keys should be at least set-up:

* `APP_URL` should point to the public URL where your application is hosted, without trailing slash
* `MAIL_*`
* `DB_*`
* `NOCAPTCHA_*`, for reCAPTCHA
  To get reCAPTCHA keys, please use the [reCAPTCHA admin console](https://www.google.com/recaptcha/admin/create) and select reCAPTCHA v2.

You can furthermore also specify your desired time zone, locale, etc.

If you wish to modify the URLs from the default course to event (or something else entirely), you can modify the following entries:
* `APP_ROUTE_CUSTOMIZED_NAMES_COURSE`
* `APP_ROUTE_CUSTOMIZED_NAMES_SUBSCRIPTIONS`
* `APP_ROUTE_CUSTOMIZED_NAMES_SUBSCRIBE`
* `APP_ROUTE_CUSTOMIZED_NAMES_UNSUBSCRIBE`

## Generating the application key

Finally, you should generate an application key. The application key is used to perform encryption and decryption routines within the application. It is also stored in the `.env` file.
You should only generate this once, and never change it again later *unless* the key gets leaked. If you regenerate the key, all sessions and signed URLs will become invalid.

{{< highlight bash >}}
php artisan key:generate
{{< / highlight >}}

## Setting up the database

The database schema is handled via migrations. These are scripts that build or upgrade your database schema incrementally in a way that can also be rolled back. If you're interested you can read more about them in the [Laravel documentation](https://laravel.com/docs/9.x/migrations).

If your database settings are correct, you should run the following command to set-up the database.
Make sure your database actually exists as this will not be created by the script!

{{< highlight bash >}}
php artisan migrate
{{< / highlight >}}

Every time you upgrade the application you should re-run the above command to make sure your database schema is always the latest version.

## Caching

To improve the performance of the application, the configuration, routes, views and icons should be cached.
You can easily to this by executing the optimize command, which internally performs the following caching commands:

{{< highlight bash >}}
php artisan config:cache
php artisan route:cache
php artisan icons:cache
php artisan view:cache
{{< / highlight >}}

## Creating an administrator user

There are no initial users provided by the application. You should therefore create an initial administrator user.
You can do so by executing the following command and following the instructions on your screen.

{{< highlight bash >}}
php artisan crepes:create-user
{{< / highlight >}}

## Next steps

Your application should now be set up and you should be able to visit the public URL and see it in action!
The next step is to set-up the cronjobs and use your administrator account to create some content.
