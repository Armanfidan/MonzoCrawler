# MonzoCrawler Design

## Requirements
- Input: Start URL
- Output: A tree data structure containing links visited.

## Restrictions
- The crawler will only crawl through subdomains, no external links.
- The crawler will only crawl through one level of subdomains.

## Remarks
- Try to make the crawler scalable.
  Make sure that we could easily add more levels of subdomains if necessary.
- Store the URLs in a tree of some sort.
  Make sure that it is easy to add levels and read from the tree.

We initialise MonzoCrawler with a single URL. MonzoCrawler will have:
1. A class `CrawlerService` to:
    - Make a request to a page,
    - Parse the HTML,
    - Pass the HTML on.

2. A class `LinkExtractor` to:
   - Receive the HTML of a webpage,
   - Remove everything other than `<Link>` and `<a>` tags (I will figure out if there is a better way to identify tags)
   - Return the links in a list.

CrawlerService will have a tree data structure as an attribute, which will store each of the links.
The service will also take in a parameter  