# James Garner Composer

This website is built using [Jekyll](https://jekyllrb.com/) and
[Bootstrap](https://getbootstrap.com/). It uses
[Markdown](https://github.github.com/gfm/) and [YAML](https://yaml.org/) for
content and data formatting.

## Pages

Pages should use a `.md` file extension in order to enable Markdown syntax.

Every page must include a
[Front Matter](https://jekyllrb.com/docs/front-matter/) section at the top of
the file containing configuration and metadata about the page. The page
**`title`** is a required field and can be defined this way:

```yaml
---
title: Page Title
---
```

(_Note: `title` needs to be enclosed in double quotes if it includes a colon._)

### Home Page

The home page content is found in [`index.md`](index.md).

The carousel quotes can be edited in [`_data/quotes.yml`](_data/quotes.yml). A
quote is a list item. The order in which the quotes are displayed is determined
by the position of the list items in the file. The quote item at the top is
displayed first, the one at the bottom displayed last.

Required fields:

- **`quotee`**: Displayed in grey below the quote `text` and prefixed by an
  M-dash. It accepts Markdown syntax.
- **`text`**: The quote text displayed in larger font size. It accepts Markdown
  syntax.

Example:

```yaml
- quotee: Person name, from some organisation
  text: Quote text.
```

(_Note: any of these fields needs to be enclosed in double quotes if it includes
a colon._)

### Biography Page

The biography page content is found in [`biography.md`](biography.md).

### Music Page

#### Music Categories

The music categories and the order in which they're displayed is defined in
[`_data/music_categories.yml`](_data/music_categories.yml). A music category
consists of an object containing a `title` field. The object ID defines the
music category ID and the `title` field the music category title.

Example:

```yaml
music_category:
  title: Music Category
```

(_Note: `title` needs to be enclosed in double quotes if it includes a colon._)

In this example, the music category ID is `music_category` and the title is
'Music Category'.

#### Music Items

Music items are a [collection](https://jekyllrb.com/docs/collections/) of files
in [`_collections/_music/`](_collections/_music/). A music item file should use
the `.md` file extension in order to enable Markdown syntax. Similar to other
pages, it must define a [Front Matter](https://jekyllrb.com/docs/front-matter/)
at the top and the item content underneath it. Music items are sorted in
descending order by year within each category.

Required fields:

- **`category`**: Must match a [music category](#music-category) ID.
- **`title`**: Displayed in bold.
- **`year`**: Displayed inside brackets and in bold next to the `title` on the
  right.

(_Note: `title` needs to be enclosed in double quotes if it includes a colon._)

Optional fields:

- **`description`**: Displayed below the `title`. It accepts Markdown syntax.
- **`footnote`**: Last paragraph displayed in grey after the music item content.
  It accepts Markdown syntax.
- **`subtitle`**: Text in grey displayed next to the `title` and `year` on the
  right. It accepts Markdown syntax.

(_Note: any of these fields needs to be enclosed in double quotes if it includes
a colon._)

Example:

```yaml
---
category: category_id
description: Music item description
footnote: Music item footnote.
subtitle: — from _Work Title_
title: Music Item Title
year: 2021
---

Music item content.
```

To add a multi-line footnote, use:

```yaml
footnote: |
  Line 1: some text.\
  Line 2.
```

(_Note: in a multi-line footnote, lines with colons don't need to be enclosed in
double quotes, as shown in 'Line 1' above._)

### Events Page

Events are [data](https://jekyllrb.com/docs/datafiles/) properties defined in
[`_data/events.yml`](_data/events.yml). They consist of objects containing list
items, where the object ID is the event category (`past` or `upcoming`). Event
list items must be defined under their respective event category. The order in
which events are displayed is determined by the position of the list items under
each category in the file. The event at the top is displayed first, the one at
the bottom displayed last. Upcoming events is the event category displayed
first by default.

Required fields:

- **`date`**: First line, displayed in grey.
- **`title`**: Displayed in bold and below the `date`. It accepts Markdown
  syntax.

(_Note: any of these fields needs to be enclosed in double quotes if it includes
a colon._)

Optional fields:

- **`country`**: Last line displayed.
- **`location`**: Displayed after the `organisation` and before the `country`.
- **`organisation`**: Displayed below the `title`.
- **`role`**: Text in grey displayed next to the `title` on the right.

(_Note: any of these fields needs to be enclosed in double quotes if it includes
a colon._)

Example:

```yaml
past:
  - country: 🇬🇧 UK
    date: Summer 1990
    location: Place Name
    organisation: Organisation
    role: — role
    title: A _Work_ Title
  - country: 🇬🇧 UK
    date: Spring 1981
    location: Place Name
    organisation: Organisation
    role: — role
    title: Event Title

upcoming:
  - country: 🇬🇧 UK
    date: 2099
    location: Place Name
    organisation: Organisation
    role: — role
    title: A _Work_ Title
```

## Plugins & Helpers

Plugins can be used in the content section of Markdown and HTML files.

### SoundCloud

To include a SoundCloud player, use:

```html.liquid
{% include soundcloud.html track_id="track_id" %}
```

Required fields:

- **`track_id`**: Can be found on SoundCloud in the embedded code after clicking
  on the 'Share' button. The track ID is in the `url` parameter following
  `https%3A//api.soundcloud.com/tracks/`.

Optional fields:

- **`height`**: A number defining the player's height in pixels (no unit
  required). Defaults to `166`.
- **`width`**: A number defining the player's width in pixels (no unit
  required). Defaults to `100%`.

### Vimeo

To include a Vimeo video, use:

```html.liquid
{% include vimeo.html video_id="video_id" %}
```

Required fields:

- **`video_id`**: Can be found in the Vimeo video URL.

### YouTube

To include a YouTube video, use:

```html.liquid
{% include youtube.html video_id="video_id" %}
```

Required fields:

- **`video_id`**: Can be found in the YouTube video URL in the `v` parameter.

### Quotes

To include a quote, use:

```html.liquid
{% include quote.html quotee="quotee" text="text" %}
```

Required fields:

- **`quotee`**: Displayed in grey below the quote text. It is indented and
  prefixed by an M-dash. It accepts Markdown syntax.
- **`text`**: The quote text, displayed indented. It accepts Markdown syntax.

(_Note: any of these fields needs to be enclosed in double quotes if it includes
a colon._)

### Image Copyright

The CSS class `image-footnote` can be applied to an HTML element underneath an
image to display small text in grey with the image copyright notice.

```html
![Image description](image_url)
<div class="image-footnote">© 2021 Image Author</div>
```

### Line Breaks

To add a line break after a paragraph in Markdown, use:

```html
Paragraph text.\
<br>

Rest of content.
```
