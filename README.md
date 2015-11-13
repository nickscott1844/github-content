# github-content [![NPM version](https://badge.fury.io/js/github-content.svg)](http://badge.fury.io/js/github-content)  [![Build Status](https://travis-ci.org/doowb/github-content.svg)](https://travis-ci.org/doowb/github-content)

> Easily retrieve raw github content.

## Install

Install with [npm](https://www.npmjs.com/)

```sh
$ npm i github-content --save
```

## Usage

```js
var githubContent = require('github-content');
```

## API

### [GithubContent](index.js#L32)

Create an instance of GithubContent to setup downloading of files.

**Params**

* `options` **{Object}**: Options to set on instance. Additional options passed to [github-base]
* `options.owner` **{String}**: Set the owner to be used for each file.
* `options.repo` **{String}**: Set the repository to be used for each file.
* `options.branch` **{String}**: Set the branch to be used for each file. Defaults to `master`

**Example**

```js
var options = {
  owner: 'doowb',
  repo: 'github-content',
  branch: 'master' // defaults to master
};

var gc = new GithubContent(options);
```

### [.owner](index.js#L63)

Set the `owner` to be used when downloading a file.

**Params**

* `owner` **{String}**: Github owner (user or organization)
* `returns` **{Object}** `this`: to enable chaining

**Example**

```js
gc.owner('doowb');
```

### [.repo](index.js#L80)

Set the `repo` to be used when downloading a file.

**Params**

* `repo` **{String}**: Github repoistory
* `returns` **{Object}** `this`: to enable chaining

**Example**

```js
gc.repo('github-content');
```

### [.branch](index.js#L97)

Set the `branch` to be used when downloading a file.

**Params**

* `branch` **{String}**: Github branch
* `returns` **{Object}** `this`: to enable chaining

**Example**

```js
gc.branch('dev');
```

### [.file](index.js#L127)

Download a single file using the previous settings and the passed in file name. File object returned will contain a `.path` property with the file path passed in and a `.content` property with the contents of the downloaded file.

**Params**

* `fp` **{String}**: file to download
* `options` **{Object}**: Additional options to base to [github-base] `.get` method.
* `cb` **{Function}**: Callback function taking `err` and `file`
* `returns` **{Object}** `this`: to enable chaining

**Example**

```js
gc.file('package.json', function(err, file) {
  if (err) return console.log(err);
  console.log(file.path);
  console.log(file.contents);
});
//=> package.json
//=> {
//=>   "name": "github-content"
//=>   ...
//=> }
```

### [.files](index.js#L173)

Download an array of files using the previous settings and the passed in file names. File objects returned will contain a `.path` property with the file path passed in and a `.content` property with the contents of the downloaded file.

**Params**

* `files` **{String|Array}**: files to download
* `options` **{Object}**: Additional options to base to [github-base] `.get` method.
* `cb` **{Function}**: Callback function taking `err` and `files`
* `returns` **{Object}** `this`: to enable chaining

**Example**

```js
gc.files(['package.json', 'index.js'], function(err, files) {
  if (err) return console.log(err);
  console.log(files.length);
  console.log(files[0].path);
  console.log(files[0].contents);
});
//=> 2
//=> package.json
//=> {
//=>   "name": "github-content"
//=>   ...
//=> }
```

## Related projects

[github-base](https://www.npmjs.com/package/github-base): Base methods for creating node.js apps that work with the GitHub API. | [homepage](https://github.com/jonschlinkert/github-base)

## Running tests

Install dev dependencies:

```sh
$ npm i -d && npm test
```

## Contributing

Pull requests and stars are always welcome. For bugs and feature requests, [please create an issue](https://github.com/doowb/github-content/issues/new).

## Author

**Brian Woodward**

+ [github/doowb](https://github.com/doowb)
+ [twitter/doowb](http://twitter.com/doowb)

## License

Copyright © 2015 Brian Woodward
Released under the MIT license.

***

_This file was generated by [verb-cli](https://github.com/assemble/verb-cli) on November 13, 2015._