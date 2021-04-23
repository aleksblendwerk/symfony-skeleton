# blendwerk/symfony-skeleton

## Introduction

This is a customized version of `symfony/website-skeleton`, the default project template used by Symfony when running 
`symfony new --full`.

The following dependencies are added on top of `symfony/website-skeleton`:

- `blendwerk/coding-standard` (comes with `squizlabs/php_codesniffer`)

- `phpstan/phpstan` and additional related packages
- `php-parallel-lint/php-parallel-lint`
- `ergebnis/composer-normalize`

- `symfony/webpack-encore-bundle`

Also the npm package [`husky`](https://github.com/typicode/husky) was added to install git hooks, the configuration
can be found in `.huskyrc.json`.

## Usage

For the highest available version:

`composer create-project blendwerk/symfony-skeleton`.

In addition to installing all composer dependencies, at the end of the initial run of `composer create-project`, the
following tasks will also be automatically executed:

- `git init`
- Install **PHPUnit** to `bin/.phpunit` (which is how Symfony handles it nowadays)
- Install all dependencies from `package.json` via `yarn install`

Some more minor tasks will be executed as well. For details, see the `post-create-project-cmd` setting in 
`composer.json`.

## Composer scripts

Some `composer` scripts are also added which can be called by running `composer <scriptname>`.

The most important ones are:

- `qa`: runs the whole suite of QA checks (also executed on `git commit`)
- `test`: runs the whole suite of tests (also executed on `git push`)

See the `scripts` section in `composer.json` for further details.

## Troubleshooting

If **PHP_CodeSniffer** reports errors, you can try to fix them automatically using `composer phpcbf`.

If **composer-normalize** reports errors, you can fix them automatically by running `composer normalize`.

## Maintenance

This needs to be updated when a new Symfony release comes out. Here is how:

Create a new branch here (for example `5.2`), get the current `composer.json` from the respective branch 
(for example `5.2`, not `master`) from https://github.com/symfony/website-skeleton and merge it with our current
`composer.json`.

The included `package.json` is based on the one included in the recipe for `symfony/webpack-encore-bundle`, the source
can be found here: https://github.com/symfony/recipes/tree/master/symfony/webpack-encore-bundle.
