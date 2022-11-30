---
tags: ["installation"]
title: "Installation"
linkTitle: "Installation"
weight: 15
description: >
  Installing the application.
---

This page will guide you on how to install the dependencies for the application.

## Download the application source code

The first step is to get a copy of the source code to the machine you want to deploy to.
At this moment, the only way to obtain it is via a git clone or download from the repository.
In the future we might add a way to install it via composer directly.

{{< highlight bash >}}
git clone https://github.com/nielsdos/crepes installation-directory
cd installation-directory
{{< / highlight >}}

## Application dependencies

We use the Composer package manager to manage our back-end (PHP) dependencies, while Yarn is used for the front-end dependencies.

### Back-end dependencies

Install the dependencies for production as follows.

{{< highlight bash >}}
composer install --no-dev
{{< / highlight >}}

> If you're setting up a development environment, you should not pass the `--no-dev` option.

### Front-end dependencies

Install the dependencies and build the front-end assets as follows.

{{< highlight bash >}}
yarn install
yarn prod
{{< / highlight >}}

> If you're setting up a development environment, you can use `yarn dev` instead of `yarn prod`. You can also use the watch option to automatically rebuild front-end assets upon changes with `yarn watch`.
