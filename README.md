# Hämta ett eller flera rss-flöden och visa på en sida

## Hur man använder Region Hallands plugin "region-halland-acf-page-rss-links-repeater"

Nedan följer instruktioner hur du kan använda pluginet "region-halland-acf-page-rss-links-repeater".


## Användningsområde

Denna plugin hämtar valfritt rss-flöde


## Installation och aktivering

```sh
A) Hämta pluginen via Git eller läs in det med Composer
B) Installera Region Hallands plugin i Wordpress plugin folder
C) Aktivera pluginet inifrån Wordpress admin
```


## Hämta hem pluginet via Git

```sh
git clone https://github.com/RegionHalland/region-halland-acf-page-rss-links-repeater.git
```


## Läs in pluginen via composer

Dessa två delar behöver du lägga in i din composer-fil

Repositories = var pluginen är lagrad, i detta fall på github

```sh
"repositories": [
  {
    "type": "vcs",
    "url": "https://github.com/RegionHalland/region-halland-acf-page-rss-links-repeater.git"
  },
],
```
Require = anger vilken version av pluginen du vill använda, i detta fall version 1.0.0

OBS! Justera så att du hämtar aktuell version.

```sh
"require": {
  "regionhalland/region-halland-acf-page-rss-links": "1.0.0"
},
```


## Visa ett eller flera rss-flöden på en sida via "Blade"

```sh
@php($myData = get_region_halland_acf_page_rss_links_items())
@foreach ($myData as $data)
  @if($data['link_data']['has_content'] == 1)
    <h2>{{$data['link_data']['rss_title']}}</h2><br>
    @foreach($data['link_data']['rss_content'] as $content)
    <a href="{{ $content['link'] }}"><strong>{!! $content['title'] !!}</strong></a><br><br>
    <p>{{ $content['description'] }}</p>
    <p><i>{{ $content['date'] }}</i></p><br>
    @endforeach
  @endif
@endforeach
```


## Versionhistorik

### 1.0.0
- Första version