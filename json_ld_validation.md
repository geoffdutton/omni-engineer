# JSON+LD Validation

A command line python tool for validating JSON+LD tags. Given a url, it should:

1. Visit the page
2. Check for `application/ld+json` tags
3. If a tag with type of `"@type":"SearchResultsPage",`, it should then crawl each search result url and save the html + json+ld tags to a file
4. If there is not a serach results page, it should save the html + json+ld tags to a file, and quit.

## Caching

Pages that are crawled should be cached in a directory with a structure like:

`.cache/<url host name>/<url path if exists>/index.html`

Given a domain like: `https://www.apartments.com/east-austin-austin-tx/`, the cache directory would be:
`.cache/www.apartments.com/east-austin-austin-tx/` with the following files:

- `.cache/www.apartments.com/east-austin-austin-tx/index.html`
- `.cache/www.apartments.com/east-austin-austin-tx/screenshot.png`
- `.cache/www.apartments.com/east-austin-austin-tx/jsonldtag1.json`
- `.cache/www.apartments.com/east-austin-austin-tx/jsonldtag2.json`

## Outputs

The tool should first output the SearchResultsPage json+ld tags to a file, and then crawl each search result url and save the html + json+ld tags to a file. Finally, each of the sub-page json+ld tags should be output in a CSV file.

Using the example above, if there were 3 pages in the search results, the output would be:

```csv
page_url, jsonld_tag_type, ...the keys of the jsonld_tag as headers
```
