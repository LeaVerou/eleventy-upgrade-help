# eleventy-upgrade-help

A plugin to help you upgrade your Eleventy project to a new version.

## Usage

**WARNING THIS PLUGIN IS IN PRERELEASE STATUS AND HAS NOT YET BEEN PUBLISHED TO NPM**

Install from npm:

```bash
npm install @11ty/eleventy-upgrade-help
```

Add to your configuration file (probably `.eleventy.js`):

```js
const UpgradeHelper = require("@11ty/eleventy-upgrade-help");

module.exports = function(eleventyConfig) {
  eleventyConfig.addPlugin(UpgradeHelper);
};
```

### Features

#### Swap from `slug` to `slugify` Filter

[_Issue 278_](https://github.com/11ty/eleventy/issues/278). Useful when you want to swap your existing use of the `slug` filter to the new `slugify` filter and want to compare any URLs that may have changed. Read more about [the `slug` to `slugify` transition on the Eleventy docs](https://www.11ty.dev/docs/filters/slugify/).

#### Data Deep Merge

[_Issue 1753_](https://github.com/11ty/eleventy/issues/1753). Warns if you do not use `eleventyConfig.setDataDeepMerge` in your configuration file that the default value has changed.

#### Liquid Options

[_Issue 1390_](https://github.com/11ty/eleventy/issues/1390)

* Warns if you use `strict_filters` instead of `strictFilters`.
* Warns if you don’t have `strict_filters` or `strictFilters` that the new default is `true`.

#### Non-root Input directory `.gitignore`

[_Issue 364_](https://github.com/11ty/eleventy/issues/364). If your input directory is not `.` and you have a `.gitignore` file inside (e.g. `src/.gitignore`), this file is no longer supported. Root project-level `.gitignore` files and input directory `.eleventyignore` files are still supported.

### Feature Opt-out

```js
const UpgradeHelper = require("@11ty/eleventy-upgrade-help");

module.exports = function(eleventyConfig) {
  eleventyConfig.addPlugin(UpgradeHelper, {
    slugToSlugify: false,
    dataDeepMerge: false,
    liquidOptions: false,
  });
};
```

<!--
Steps:

1. Check eleventy version of current project to make sure it’s relevant.
2. Run the assigned ruleset specific to your project.
3. Show errors and warnings
4. If no errors or warnings, show a message to remove the plugin.
-->