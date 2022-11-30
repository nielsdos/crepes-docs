---
title: "Contribution Guidelines For The Project"
linkTitle: "Contribution Guidelines For The Project"
weight: 10
description: >
  How to contribute to the project
---

Please always target the `develop` branch in your pull requests.

If you don't know where to start, you can always try to look at the open issues in the repository to find missing features or bugs that should be fixed.

If you don't have a particular feature of bugfix in mind, but would still like to make a contribution, you can always check the roadmap and work on something you feel is missing from the project.

## Setting up a development environment

You can follow the same installation instructions for a production environment, except for the following changes.

### Updating `.env`

It is recommended to change the `.env` file to have the following properties set:

```
APP_ENV=development
APP_DEBUG=true
```

### Installing development dependencies

Do *not* pass `--no-dev` to the composer install command line:

```
composer install
```

Front-end dependencies can be installed with:

```
yarn install
```

## Developing

You can start the built-in Laravel server using:
```
php artisan serve
```

To make changes to the front-end JavaScript and CSS code, you should be using:
```
yarn watch
```
to watch for changes and automatically rebuild the affected front-end files.

## Testing

We use PHPUnit as our testing framework with a test database called `courses_testing`. Make sure to setup an empty database with that name in order to run the tests. Please make sure to include regression tests if you are fixing a bug, or feature tests when adding a new feature.

To run the tests, use:

```
vendor/bin/phpunit
```

If you wish to generate a coverage report whilst running the tests, you can use:

```
php artisan view:clear;XDEBUG_MODE=coverage vendor/bin/phpunit --coverage-html reports
```

## Static analysis

We use the PHPStan static analyser tool to find bugs earlier. We recommend that you run the tool and fix any errors that pop up by your changes before opening a pull request.

To run the tool you can use:

```
vendor/bin/phpstan analyse --memory-limit=1G
```
