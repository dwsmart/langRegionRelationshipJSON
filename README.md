# langRegionRelationship
## A JSON based hreflang alternative for multilingual websites
### Introduction
Currently, the most common way to implement hreflang tags is to include them in the head of the HTML document, like this:
```html
<link rel="alternate" href="http://example.com/" hreflang="en" />
<link rel="alternate" href="http://example.com/de/" hreflang="de" />
<link rel="alternate" href="http://example.com/fr/" hreflang="fr" />
```
In HTTP headers, the hreflang tags can be included like this:
```html
Link: <http://example.com/>; rel="alternate"; hreflang="en",
      <http://example.com/de/>; rel="alternate"; hreflang="de",
      <http://example.com/fr/>; rel="alternate"; hreflang="fr"
```
Or in the sitemap:
```html
<url>
  <loc>http://example.com/</loc>
  <xhtml:link rel="alternate" hreflang="en" href="http://example.com/" />
  <xhtml:link rel="alternate" hreflang="de" href="http://example.com/de/" />
  <xhtml:link rel="alternate" hreflang="fr" href="http://example.com/fr/" />
</url>
```
Although these methods are widely used, they have some limitations. For example, for pages with a large amount of URLs and languages, and the requirement for URLs to be reciprocal, the implementation can be quite complex.


### The langRegionRelationship alternative
The langRegionRelationship is a JSON object that contains the language-region relationships for each URL. Here is a proposed example of a langRegionRelationship object:

_(Comments are not supported in JSON, so if you wanted to add explainers to the code, you could add a "comment{x}" key:value pair, as in this example)_
```html
<script type="langRegionRelationship">
{
    "langRegion": [
        {
            "scope": {
                "include": "*",
                "comment": "the scope of the langRegionRelationship object, in this case, all URLs on the website, follows familiar https://en.wikipedia.org/wiki/Path_(computing)",
                "exclude": "/checkout/*",
                "comment2": "excludes the checkout section of the website from the langRegionRelationship object"
            },
            "xHost": "https://example.com",
            "comment": "the default host if no region / lang rules apply, similar in concept to x-default hreflang, If the host is different for a specific region, it can be defined in the regionTarget object. If a site only has one host, the xHost field can be omitted and assumed it's the current host",
            "xUrl": "/en-GB/content.html",
            "comment2": "the default url if no region / lang rules apply, similar in concept to x-default hreflang",
            "langRegionTarget": {
                "comment": "allows for combination of international targeting & language targeting",
                "patternURL": "/{lang}-{region}/*",
                "comment2": "Allow pattern matching for the URL, {lang} and {region} are placeholders for the language and country codes, * is a wildcard for the rest of the URL",
                "alternates": [
                    {
                        "regionTarget": "GB, US, AU",
                        "comment": "multiple countries, one language",
                        "langs": [
                            {
                                "lang": "en",
                                "comment": "no url field, relies on the pattern matching above, English in Australia would calculate as https://example.com/en-AU/content.html"
                            }
                        ]
                    },
                    {
                        "regionTarget": "BR",
                        "host": "https://example.com.br",
                        "patternURL": "/{lang}/*",
                        "comment": "single country, multiple languages, but on a different host, uses the pattern matching above.",
                        "langs": [
                            {
                                "lang": "pt",
                                "comment": "no url field, relies on the pattern matching above, Portuguese in Brazil would calculate as https://example.com.br/pt/content.html"
                            },
                            {
                                "lang": "en, *",
                                "comment": "no url field, relies on the pattern matching above, English in Brazil would calculate as https://example.com.br/en/content.html"
                            },
                            {
                                "lang": "*",
                                "follows": "en",
                                "comment": "wild card, all none matched languages in Brazil. The follows specifies to follow the en rules. Will specify https://example.com.br/en/content.html, overruling the xUrl field, as it is more specific"
                            }
                        ]
                    },
                    {
                        "regionTarget": "CA",
                        "comment": "uses url field because there is a different structure / domains in Canada, overruling the pattern matching above, applicable only to this URL",
                        "langs": [
                            {
                                "lang": "en",
                                "url": "https://example.ca/canadian-content.html"
                            },
                            {
                                "lang": "fr",
                                "url": "https://example.ca/contenu-canadien.html"
                            }
                        ]
                    }
                ]
            }
        }
    ]
}
</script>
``` 

I propose that this could also be a separate file, and included like this, with the same content as above (minus the script tags):
```html
<script src="/langRegionRelationship.json" type="langRegionRelationship"></script>
```

Or altenratively, the langRegionRelationship object could be included in the HTTP headers, like this:
```html
Link: <https://example.com/langRegionRelationship.json>; rel="langRegionRelationship"
```
To enable usage for non-HTML documents, such as PDFs, images, or other file types

Cross-domain relationships could be defined in the langRegionRelationship object, and the langRegionRelationship object could be included in the HTTP headers of the document, or in the document itself, as above, to allow for cross-domain relationships to be defined in the langRegionRelationship object, all pointing to the same langRegionRelationship object on one hostname. For example:

`https://example.com/`:
```html
<script src="/langRegionRelationship.json" type="langRegionRelationship"></script>
```
`https://example.ca/`:
```html
<script src="https://example.com/langRegionRelationship.json" type="langRegionRelationship"></script>
```
`https://de.example.com/`:
```html
<script src="https://example.com/langRegionRelationship.json" type="langRegionRelationship"></script>
```
and so on.

You could also then include different rules for different parts of your site, for example, perhaps a blog section of your site has one format, so for that you could include a different langRegionRelationship object, like this:
```html
<script src="/blog/LangRegionRelationship.json" type="langRegionRelationship"></script>
```

You can then combine both methods, for example, if you have a large number of URLs and languages, you could use the JSON object to define the relationships, and then include the JSON object in the HTML document like above for most documents, and then if there are edge cases and exceptions, you could include rules that are specific to that group of documents.
```html
<script src="/langRegionRelationship.json" type="langRegionRelationship">
{
    "langRegion": [
        {
            "comment": "This one has a spanish translation too",
            "langRegionTarget": {
                "alternates": [
                    {
                        "regionTarget": "*",
                        "comment": "wildcard for all regions, could also omit regionTarget, as all regions should be assumed to be included unless otherwise specified",
                        "langs": [
                            {
                                "lang": "en",
                                "url": "https://example.com/spanish.html"
                            }
                        ]
                    }
                ]
            }
        }
    ]
}
</script>
```
Or this page is only available in one language, so you want to exclude it from the langRegionRelationship rules:
```html
<script src="/langRegionRelationship.json" type="langRegionRelationship">
{
    "langRegion": FALSE
}
</script>
```

This mechanism of separate file and the ability to override the rules in the HTML document is similar to how the [Speculation Rules API](https://developer.mozilla.org/en-US/docs/Web/API/Speculation_Rules_API) works, so it could be familiar to developers.
## How a Search Engine should interpret the langRegionRelationship object
using the example above, the search engine should interpret the langRegionRelationship object as follows:

| URL returned as relevant document | Language of a User | Region of a User | URL to Display in SERP|
| --- | ------------------ | ---------------- | ------------------ |
| https://example.com/en-GB/content.html | English | United Kingdom | https://example.com/en-GB/content.html, it's the right combination |
| https://example.com/en-US/content.html | English | United Kingdom | https://example.com/en-GB/content.html, wrong region, show the UK |
| https://example.com/content.html | English | Australia | https://example.com/content.html, the URL doesn't match the pattern expected for {lang}-{region} so is unaffected by the `langRegionRelationship` rules |
| https://example.com/en-GB/content.html | Portuguese | Brazil | https://example.com.br/pt/content.html |
| https://example.ca/canadian-content.html | French | Canada | https://example.ca/contenu-canadien.html, there is a specific rule to specify this direct relationship |

## Looks... Complex...
Yes, the examples above are quite complex, but the idea is that the langRegionRelationship object can be as simple or as complex as needed. For a more common use case, the object could be as simple as this, on all pages of a website include 
```html
<script src="langRegionRelationship.json" type="langRegionRelationship">
</script>
```
and in the root of the site have a `langRegionRelationship.json` file that contains:
```json
{
    "langRegion": [
        {
            "scope": {
                "include": "*"
            },
            "langRegionTarget": {
                "patternURL": "/{lang}-{region}/*",
                "alternates": [
                    {
                        "regionTarget": "GB, US, AU",
                        "langs": [
                            {
                                "lang": "en"
                            }
                        ]
                    },
                    {
                        "regionTarget": "*",
                        "patternURL": "/{lang}/*",
                        "langs": [
                            {
                                "lang": "de, en, es, fr, it, pt"
                            }
                        ]
                    }
                ]
            }
        }
    ]
}
```

This would be a simple way to implement the langRegionRelationship object, and would be a more efficient way to implement hreflang tags for a website with a large number of URLs and languages. Added Dutch translations to the website? Just change the `langRegionRelationship.json` file, adding nl.
```json
{
    "langRegion": [
        {
            "scope": {
                "include": "*"
            },
            "langRegionTarget": {
                "patternURL": "/{lang}-{region}/*",
                "alternates": [
                    {
                        "regionTarget": "*",
                        "patternURL": "/{lang}/*",
                        "langs": [
                            {
                                "lang": "de, en, es, fr, it, nl, pt"
                            }
                        ]
                    }
                ]
            }
        }
    ]
}
``` 
It will be taken into account for  all URLs on the website that fit any of the patterns specified in the `langRegionRelationship.json` file.

There will always be some complexity, but the langRegionRelationship object is designed to be as simple or as complex as needed, and to be flexible enough to handle a wide range of multilingual websites.

CMSs could also generate the `langRegionRelationship.json` file automatically, and handle any required overrides based on the languages and regions that are available on the website, and the URLs that are available for each language and region, with no real extra overhead vs. the current hreflang implementation methods.

There could also be simple to use tools to generate the `langRegionRelationship.json` file and associated markup, provided by the search engines themselves, and/or by third parties, to make it easier for webmasters to implement the langRegionRelationship object on their websites.

## Objections / Questions
### Does it solve the reciprocal URL problem?
No, at least not entirely. It doesn't solve the reciprocal URL problem, that's more of a security issue, especially cross-domain, otherwise one could hijack the language / and or region of someone else's website, by claiming in your markup that you're the alternate version of their website.

However, it does make it easier to implement the reciprocal relationship, especially if you're using an external, as a search engine can see all sites reference the same file on the same host.

### Does it solve the problem of having to have unique URLs for each language and region?
No, it doesn't solve that problem, but there realistically isn't a way to solve that problem, as a search engine needs to land someone on a specific URL.

### Does it solve the problem of having to have language-region specific URLs crawled by search engines?
No, it doesn't solve that problem, because a search engine would want to crawl the language-region specific URLs to:
- Understand if that URL actually exists, it's a poor experience for their users to land on a 404 page
- Understand the content of the page, to make sure it's genuinely a translation / suitable alternative for the user, and to minimise bad actors trying to game the system, almost a kind of cloaking, but for language / region instead of user-agent.

### Does it solve the problem of having to include hreflang tags on every page?
Partially, you do need to call the `langRegionRelationship.json` file on every page, but you don't need to include the rules on every page, you can include the rules in the `langRegionRelationship.json` file, and then include the file on every page, and then only include the rules on the pages where you need to override the rules in the `langRegionRelationship.json` file.

### What about Synchronicity?
This is a downside, in theory, URLs could be changed before a search engine had fetched and processed the changed `langRegionRelationship.json` file. This does seem be a fair trade-off for the simplicity and flexibility of the langRegionRelationship object.

### What about adding to page weight?
If the `langRegionRelationship.json` file is used, it would reduce the page weight, especially for large websites with many URLs and languages, as one `langRegionRelationship.json` file would be smaller than the equivalent hreflang tags, and would only need to be included once on each page, rather than on every page.

In additon, `<script>` tags with `type="langRegionRelationship"` would be ignored by browsers, as `<script>` tags without a type of `javascript` (or no type), `module`,`importmap` or `speculationrules` are not processed by the browser, so the `langRegionRelationship.json` file would not be fetched. (see [MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/script/type))

## Going Forward
One of the issues with hreflang is that to date, it's only been supported by Google and  Yandex, and not by other search engines. And it's only for search engines. A proper spec could be developed, and if adopted used by other agents too, such as browsers, screen readers, to help users navigate a website in their preferred language, if the site offers it.

## Couple of examples
Some examples of how the langRegionRelationship object could be used in practice on real websites [can be found here](/example/README.md).


## Some other proposals
- A robots.txt based on from Aleyda Solís' [post on linkedin](https://www.linkedin.com/posts/aleyda_so-gary-illyes-asked-for-alternatives-to-activity-7192287485190664192-wCU-)

_Let me know if you have any other proposals, and I'll add them here!_


## Feedback? Ideas? Improvements?
[Open an issue](https://github.com/dwsmart/langRegionRelationshipJSON/issues), or a pull request! I'd love to hear your thoughts on this proposal, and how it could be improved, or if you have any other ideas for how to improve the implementation of alternates tags on multilingual websites.