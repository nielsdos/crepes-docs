---
tags: ["installation"]
title: "Cronjobs"
linkTitle: "Cronjobs"
weight: 25
description: >
  Setting up the cronjobs for the application.
---

Cronjobs are a way to automatically execute scheduled commands.
They are used in the application to run jobs from the queue such as sending notification emails, and also to send reminders.

## A note on the queue

If you plan on listening to the queue using Laravel's built-in tools instead of using a scheduled job, you can use the following command instead of setting up a cronjob *for the queue*. A cronjob to send reminders is still necessary.

{{< highlight bash >}}
php artisan queue:listen
{{< / highlight >}}

## Cronjob configuration

The following two jobs should be run:

* `php artisan queue:work --stop-when-empty --tries=5`
* `php artisan crepes:send-reminders`

An example crontab configuration could look like:

{{< highlight crontab >}}
0 10 * * * cd installation_directory && php artisan subreminders:send >> /dev/null 2>&1
*/20 * * * * cd installation_directory && php artisan queue:work --stop-when-empty --tries=5 >> /dev/null 2>&1
{{< / highlight >}}

> Make sure to replace `installation_directory` with your installation directory!
