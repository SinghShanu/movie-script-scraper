# MSS

[![stars][stars]][stars-url]
[![pr][pr]][pr-url]
[![license][license]][license-url]
[![twitter][twitter]][twitter-url]

MSS "Movie Script Scrapper" - A simple scrapper to retrieve scripts by genre from IMSDB.

# Installation

```bash
$ npm install -S mss
```

# Usage

## Example Usage

**MSS** exposes a function; simply pass this function the options (see below), and it will return a promise with the file paths of the scripts it saved.

```javascript
var mss = require('mss');

var options = {
	genre: 'Action',
	total: 10,
};

mss(options)
	.then(filePaths => {
		console.log(filePaths);
	})
	.catch(err => {
		console.error('There was a problem');
	});
```

### Options

* `genre` [__string__] - Any valid film genre, a complete list can be found [here](https://github.com/JoeKarlsson/movie-script-scrapper/blob/master/src/helper/isValidGenre.js).
  * Defaults to "Action".
* `total` [__number__] - the total number of scripts you want from a given genre.
  * Defaults to 10.
* `title` [__string__] - The name of the film's script you want.
* _TODO_ - `scriptDir` [string] - Location that you want to save your scripts.
  * Defaults to ./scripts

## Running from command line

You can run MSS directly from the CLI (if it's globally available in your PATH, e.g. by `npm install -g mss`) with variety of useful options.

```bash
$ mss --total 10 --genre Comedy
```

or enter a title:

```bash
$ mss --title 'american sniper'
```

# How it Works

Conveniently IMSDB provides RSS feeds based on movie genre (ex. <http://www.imsdb.com/feeds/genre.php?genre=Comedy>). Using the awesome fetch module we are then able to grab that page and use a regular expression to generate an array of movie script URLs. We then visit each URL with Fetch and use another awesome module called Cheerio to select just the movie script from each page and finally output each script to a file.

## Running Locally

1. Install dependencies with:

```bash
$ npm install -S mss
```

1. Run Tests

```bash
$ npm test
```

## Contributing

1. Fork it!
1. Create your feature branch: `git checkout -b my-new-feature`
1. Commit your changes: `git commit -am 'Add some feature'`
1. Push to the branch: `git push origin my-new-feature`
1. Submit a pull request :D

### Maintainers

<table>
  <tbody>
    <tr>
      <td align="center">
        <img width="150 height="150"
        src="https://avatars.githubusercontent.com/JoeKarlsson?v=3">
        <br />
        <a href="https://github.com/JoeKarlsson">Joe Karlsson</a>
      </td>
    <tr>
  <tbody>
</table>

### License

#### [MIT](./LICENSE)

[pr]: https://img.shields.io/badge/PRs-welcome-brightgreen.svg
[pr-url]: CONTRIBUTING.md
[stars]: https://img.shields.io/github/stars/JoeKarlsson/movie-script-scrapper.svg?style=flat-square
[stars-url]: https://github.com/JoeKarlsson/movie-script-scrapper/stargazers
[license]: https://img.shields.io/github/license/JoeKarlsson/movie-script-scrapper.svg
[license-url]: https://github.com/JoeKarlsson/movie-script-scrapper/blob/master/LICENSE
[twitter]: https://img.shields.io/twitter/url/https/github.com/JoeKarlsson/movie-script-scrapper.svg?style=social&style=flat-square
[twitter-url]: https://twitter.com/intent/tweet?text=Movie%20Site%20Scrapper:&url=https%3A%2F%2Fgithub.com%2FJoeKarlsson%2Fmovie-script-scrapper
