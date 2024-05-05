# Real World Comparisons

## Example 1 Adidas's `hreflang` tags

Here's a practical comparison of the two methods, using the example of Adidas's website. I chose Adidas because they have a large number of `hreflang` tags on their website, and a mix of tld and subfolder structures, representing a good variety of use cases.

Currently, Adidas has 78 `hreflang` tags on their website:
```html
<link rel="alternate" href="https://www.adidas.com.ar" hrefLang="es-AR">
<link rel="alternate" href="https://www.adidas.at" hrefLang="de-AT">
<link rel="alternate" href="https://www.adidas.com.au" hrefLang="en-AU">
<link rel="alternate" href="https://www.adidas.be/en" hrefLang="en-BE">
<link rel="alternate" href="https://www.adidas.be/fr" hrefLang="fr-BE">
<link rel="alternate" href="https://www.adidas.be/nl" hrefLang="nl-BE">
<link rel="alternate" href="https://www.adidas.com.br" hrefLang="pt-BR">
<link rel="alternate" href="https://www.adidas.ca/en" hrefLang="en-CA">
<link rel="alternate" href="https://www.adidas.ca/fr" hrefLang="fr-CA">
<link rel="alternate" href="https://www.adidas.ch/de" hrefLang="de-CH">
<link rel="alternate" href="https://www.adidas.ch/en" hrefLang="en-CH">
<link rel="alternate" href="https://www.adidas.ch/fr" hrefLang="fr-CH">
<link rel="alternate" href="https://www.adidas.ch/it" hrefLang="it-CH">
<link rel="alternate" href="https://www.adidas.cl" hrefLang="es-CL">
<link rel="alternate" href="https://www.adidas.co" hrefLang="es-CO">
<link rel="alternate" href="https://www.adidas.cz" hrefLang="cs-CZ">
<link rel="alternate" href="https://www.adidas.de" hrefLang="de-DE">
<link rel="alternate" href="https://www.adidas.de/en" hrefLang="en-DE">
<link rel="alternate" href="https://www.adidas.dk" hrefLang="da-DK">
<link rel="alternate" href="https://www.adidas.es" hrefLang="es-ES">
<link rel="alternate" href="https://www.adidas.fi" hrefLang="en-FI">
<link rel="alternate" href="https://www.adidas.fr" hrefLang="fr-FR">
<link rel="alternate" href="https://www.adidas.gr" hrefLang="el-GR">
<link rel="alternate" href="https://www.adidas.ie" hrefLang="en-IE">
<link rel="alternate" href="https://www.adidas.co.in" hrefLang="en-IN">
<link rel="alternate" href="https://www.adidas.it" hrefLang="it-IT">
<link rel="alternate" href="https://www.adidas.co.kr" hrefLang="ko-KR">
<link rel="alternate" href="https://www.adidas.mx" hrefLang="es-MX">
<link rel="alternate" href="https://www.adidas.com.my/en" hrefLang="en-MY">
<link rel="alternate" href="https://www.adidas.nl" hrefLang="nl-NL">
<link rel="alternate" href="https://www.adidas.no" hrefLang="no-NO">
<link rel="alternate" href="https://www.adidas.co.nz" hrefLang="en-NZ">
<link rel="alternate" href="https://www.adidas.pe" hrefLang="es-PE">
<link rel="alternate" href="https://www.adidas.com.ph" hrefLang="en-PH">
<link rel="alternate" href="https://www.adidas.pl" hrefLang="pl-PL">
<link rel="alternate" href="https://www.adidas.pt" hrefLang="pt-PT">
<link rel="alternate" href="https://www.adidas.se" hrefLang="sv-SE">
<link rel="alternate" href="https://www.adidas.com.sg" hrefLang="en-SG">
<link rel="alternate" href="https://www.adidas.sk" hrefLang="sk-SK">
<link rel="alternate" href="https://www.adidas.co.th/en" hrefLang="en-TH">
<link rel="alternate" href="https://www.adidas.co.th/th" hrefLang="th-TH">
<link rel="alternate" href="https://www.adidas.com.tr/en" hrefLang="en-TR">
<link rel="alternate" href="https://www.adidas.com.tr/tr" hrefLang="tr-TR">
<link rel="alternate" href="https://www.adidas.co.uk" hrefLang="en-GB">
<link rel="alternate" href="https://www.adidas.com/us" hrefLang="en-US">
<link rel="alternate" href="https://www.adidas.com.vn/en" hrefLang="en-VN">
<link rel="alternate" href="https://www.adidas.com.vn/vi" hrefLang="vi-VN">
<link rel="alternate" href="https://www.adidas.ae/en" hrefLang="en-AE">
<link rel="alternate" href="https://www.adidas.com/ke" hrefLang="en-KE">
<link rel="alternate" href="https://www.adidas.com/gh" hrefLang="en-GH">
<link rel="alternate" href="https://www.adidas.com/lk" hrefLang="en-LK">
<link rel="alternate" href="https://www.adidas.com/ng" hrefLang="en-NG">
<link rel="alternate" href="https://www.adidas.com/tz" hrefLang="en-TZ">
<link rel="alternate" href="https://www.adidas.com/iq" hrefLang="en-IQ">
<link rel="alternate" href="https://www.adidas.com/kw/en" hrefLang="en-KW">
<link rel="alternate" href="https://www.adidas.com/om/en" hrefLang="en-OM">
<link rel="alternate" href="https://www.adidas.com/bh/en" hrefLang="en-BH">
<link rel="alternate" href="https://www.adidas.co.za" hrefLang="en-ZA">
<link rel="alternate" href="https://www.adidas.co.il/en" hrefLang="en-IL">
<link rel="alternate" href="https://www.adidas.sa/en" hrefLang="en-SA">
<link rel="alternate" href="https://www.adidas.com/qa/en" hrefLang="en-QA">
<link rel="alternate" href="https://www.adidas.com/dz/fr" hrefLang="fr-DZ">
<link rel="alternate" href="https://www.adidas.com/tn/fr" hrefLang="fr-TN">
<link rel="alternate" href="https://www.adidas.com/sn/fr" hrefLang="fr-SN">
<link rel="alternate" href="https://www.adidas.com/ci/fr" hrefLang="fr-CI">
<link rel="alternate" href="https://www.adidas.com/ao/pt" hrefLang="pt-AO">
<link rel="alternate" href="https://www.adidas.com/ec/es" hrefLang="es-EC">
<link rel="alternate" href="https://www.adidas.com/cr/es" hrefLang="es-CR">
<link rel="alternate" href="https://www.adidas.co.il/he" hrefLang="he-IL">
<link rel="alternate" href="https://www.adidas.sa/ar" hrefLang="ar-SA">
<link rel="alternate" href="https://www.adidas.com/qa/ar" hrefLang="ar-QA">
<link rel="alternate" href="https://www.adidas.com.eg/ar" hrefLang="ar-EG">
<link rel="alternate" href="https://www.adidas.com.eg/en" hrefLang="en-EG">
<link rel="alternate" href="https://www.adidas.com/kw/ar" hrefLang="ar-KW">
<link rel="alternate" href="https://www.adidas.com/bh/ar" hrefLang="ar-BH">
<link rel="alternate" href="https://www.adidas.com/om/ar" hrefLang="ar-OM">
<link rel="alternate" href="https://www.adidas.co.ma/fr" hrefLang="fr-MA">
<link rel="alternate" href="https://www.adidas.co.ma/ar" hrefLang="ar-MA">
```

Using  the langRegionRelationship object approach, these could be represented in this JSON file: [adidas-langRegionRelationship.json](adidas-langRegionRelationship.json)

This file has 78 keys, each representing a URL, and each key has an array of hreflang values. This represents the same array of urls and lang / region values, but in just **50** (48 `alternates:`, 1 `scope:`, 1 `xHost:`) rules.

hreflang would need to appear on each page on each variant, but the langRegionRelationship file would only need to exist once, and imported globally on each page on each variant like so:
```html
<script src="langRegionRelationship.json" type="langRegionRelationship"></script>
```

This would, in my view, be a significant reduction in the amount of code needed to represent the same data, and would be easier to maintain and update.

## Example 2 Doc Martens's `hreflang` tags
This represents a good example of a website that targets some countries as an EU region, and some as individual countries. 

Doc Martens has 38 `hreflang` tags on their website:
```html
<link rel="alternate" hreflang="fi-fi" href="https://www.drmartens.com/fi/fi/" />
<link rel="alternate" hreflang="de" href="https://www.drmartens.com/de/de/" />
<link rel="alternate" hreflang="en-ie" href="https://www.drmartens.com/eu/en_eu/" />
<link rel="alternate" hreflang="en-us" href="https://www.drmartens.com/us/en/" />
<link rel="alternate" hreflang="en-ca" href="https://www.drmartens.com/ca/en_ca/" />
<link rel="alternate" hreflang="fi" href="https://www.drmartens.com/fi/fi/" />
<link rel="alternate" hreflang="en-ee" href="https://www.drmartens.com/eu/en_eu/" />
<link rel="alternate" hreflang="fr" href="https://www.drmartens.com/fr/fr/" />
<link rel="alternate" hreflang="nl-be" href="https://www.drmartens.com/nl/nl/" />
<link rel="alternate" hreflang="en-gr" href="https://www.drmartens.com/eu/en_eu/" />
<link rel="alternate" hreflang="de-at" href="https://www.drmartens.com/de/de/" />
<link rel="alternate" hreflang="nl-nl" href="https://www.drmartens.com/nl/nl/" />
<link rel="alternate" hreflang="en-cz" href="https://www.drmartens.com/eu/en_eu/" />
<link rel="alternate" hreflang="en-ro" href="https://www.drmartens.com/eu/en_eu/" />
<link rel="alternate" hreflang="en-pl" href="https://www.drmartens.com/eu/en_eu/" />
<link rel="alternate" hreflang="de-de" href="https://www.drmartens.com/de/de/" />
<link rel="alternate" hreflang="en-nl" href="https://www.drmartens.com/eu/en_eu/" />
<link rel="alternate" hreflang="sv" href="https://www.drmartens.com/se/se/" />
<link rel="alternate" hreflang="en-be" href="https://www.drmartens.com/eu/en_eu/" />
<link rel="alternate" hreflang="en-bg" href="https://www.drmartens.com/eu/en_eu/" />
<link rel="alternate" hreflang="es-es" href="https://www.drmartens.com/es/es/" />
<link rel="alternate" hreflang="en-pt" href="https://www.drmartens.com/eu/en_eu/" />
<link rel="alternate" hreflang="it" href="https://www.drmartens.com/it/it/" />
<link rel="alternate" hreflang="en-lu" href="https://www.drmartens.com/eu/en_eu/" />
<link rel="alternate" hreflang="en-lt" href="https://www.drmartens.com/eu/en_eu/" />
<link rel="alternate" hreflang="es" href="https://www.drmartens.com/es/es/" />
<link rel="alternate" hreflang="en-lv" href="https://www.drmartens.com/eu/en_eu/" />
<link rel="alternate" hreflang="it-it" href="https://www.drmartens.com/it/it/" />
<link rel="alternate" hreflang="en-hu" href="https://www.drmartens.com/eu/en_eu/" />
<link rel="alternate" hreflang="fr-be" href="https://www.drmartens.com/fr/fr/" />
<link rel="alternate" hreflang="sv-se" href="https://www.drmartens.com/se/se/" />
<link rel="alternate" hreflang="da-dk" href="https://www.drmartens.com/dk/da/" />
<link rel="alternate" hreflang="fr-fr" href="https://www.drmartens.com/fr/fr/" />
<link rel="alternate" hreflang="en-sl" href="https://www.drmartens.com/eu/en_eu/" />
<link rel="alternate" hreflang="en-sk" href="https://www.drmartens.com/eu/en_eu/" />
<link rel="alternate" hreflang="da" href="https://www.drmartens.com/dk/da/" />
<link rel="alternate" hreflang="en-gb" href="https://www.drmartens.com/uk/en_gb/" />
<link rel="alternate" hreflang="nl" href="https://www.drmartens.com/nl/nl/" />
```

This can be represented in the langRegionRelationship object like so: [drmartens-langRegionRelationship.json](drmartens-langRegionRelationship.json)
 and represents just **10** (8 `alternates:`, 1 `scope:`, 1 `xHost:`) rules.
