# Ember & Oak — design and presentation notes

A fictional fire-driven restaurant website created as a single-page HTML and CSS course project. All restaurant details, dishes and prices are invented for this assignment.

## Files and opening the site

```text
restaurant/
├── index.html              Page content and structure
├── style.css               Colours, layout and responsive styles
├── images/                 Five local Pexels photographs
│   ├── fire.jpg            Hero image
│   ├── room.jpg            Dining room 
│   ├── rice.jpg            Ember risotto
│   ├── grill.jpg           Hearth-grilled fish
│   └── sweet.jpg           Smoked pear dessert
├── video/
│   └── kitchen.mp4   Local cooking video
├── home-wireframe.svg      Clear desktop and mobile homepage wireframe
├── presentation-practice.md  Classroom presentation and live-edit practice
└── README.md               Design notes and media credits
```

Open `index.html` in a modern browser. Keep the entire folder together: the HTML uses relative paths to the CSS, photographs and video. The page, images, system fonts and video do not require an internet connection. The source and licence links in the video credit and this document do require internet access. The form is deliberately a demonstration: the button is disabled and no message is sent or saved.

## 1. Simple homepage wireframe

Open [home-wireframe.svg](home-wireframe.svg) for a clear desktop and mobile diagram. See [presentation-practice.md](presentation-practice.md) for a classroom walkthrough and live-edit practice.

Desktop first screen (on a phone the navigation wraps and the content stacks in one column):

```text
┌──────────────────────────────────────────────────────────────┐
│ ✳ Ember & Oak   Home  About  Products/Services  [Book a tbl] │
├──────────────────────────────────────────────────────────────┤
│                full-width fire photograph                    │
│            WOOD · SMOKE · FLAME                              │
│        Everything we cook passes through fire.               │
│        [ See the menu ]  [ Book a table ]                    │
│ Tue–Sat from 5:30 pm | 24 Oak Lane | Walk-ins at the bar     │
└──────────────────────────────────────────────────────────────┘
   ↓ About (story + stats) → Menu (course rows) → Experience
     (+ video) → Contact (form + details) → Footer
```

## 2. Colour palette

| Role | Colour | Hex |
|---|---|---|
| Page background and footer | Coal | `#151110` |
| Menu and contact background | Char | `#1E1815` |
| Panels and rules | Ash | `#2A221D` |
| Main text | Bone | `#F1EADD` |
| Supporting text | Stone | `#B8A993` |
| Buttons and accents | Flame | `#C98A3D` |
| Headings, highlights and focus | Gold | `#E0B269` |
| Small print | Dim | `#A99A88` |

All colours are defined as variables at the top of `style.css`, so changing one value updates the whole site.

## 3. Typography

- **Headings and wordmark:** Georgia, with Times New Roman and a generic serif as fallbacks. The italic style adds an editorial, flame-lit quality.
- **Body, navigation and buttons:** Arial, with Helvetica and a generic sans-serif as fallbacks. These familiar system fonts keep the site readable without a font download.

The exact appearance may vary slightly between devices depending on installed fonts.

## 4. Audience and design concept

The site is aimed at diners who enjoy theatrical, seasonal cooking: a small dining room built around one open wood fire, twelve tables and no gas or electric ovens. The design uses a dark, ember-lit palette, oversized serif headlines with a gold italic second line, numbered kicker rows (01 / 04 …) and thin rules that separate each chapter of the page. The menu reads as three wide rows — number, photo, description, price — rather than a grid of cards.

### Four design principles

- **Contrast:** light bone type and gold accents stand out against the coal and char backgrounds; the darker menu and contact sections mark the change in the page journey.
- **Repetition:** Georgia headings with italic gold lines, the uppercase letter-spaced overlines and the warm ember palette recur across every section.
- **Alignment:** a shared `.section-wrap` width and the kicker rows give the varied image and text layouts a common edge.
- **Proximity:** each course row keeps its number, photo, description and price together; contact labels sit next to their form fields and details.

## 5. How the code works

- `index.html` contains a sticky header and navigation, then `main` with Home (hero), About, Menu, Experience and Contact sections, followed by a footer. Each navigation `href` points to the matching section `id`.
- The hero places the headline over a full-width photograph with a gradient overlay, plus an info strip of opening hours and address.
- The three menu `article.course` elements group a number, photograph, dish title, description and price. The `alt` attributes describe the images.
- The native `<video controls>` element embeds the local WebM file. It has a poster, an accessible label, and a download fallback. The credit below it links to the original and its licence.
- Every form field has a matching `<label for="…">` and input `id`. The button is `type="button"` and disabled because there is no submission service.
- `style.css` starts with colour variables, then styles the header, hero, sections, form and footer. CSS Grid and Flexbox organise columns and alignment. The media queries at `800px` and `600px` adapt the layout to narrower screens. Images use `max-width: 100%` and `object-fit: cover` to fit their containers.
- Keyboard focus outlines and a skip link support navigation. Reduced-motion settings disable smooth scrolling.

## 6. Four live-edit examples

1. **Change a colour:** at the top of `style.css`, change `--flame:#c98a3d;` to another hex value such as `--flame:#d9a24a;`. Save and refresh to see buttons and accents change.
2. **Change a heading:** in `index.html`, find the `h1` containing `Everything we cook` and replace the text inside it. Keep the `<h1>`, `<br>` and `<i>` tags if you want to retain the same structure and styling.
3. **Change an image:** put a suitable new photo in `images/`, then replace `src="images/fire.jpg"` with its new path, for example `src="images/hearth.jpg"`. Update the `alt` description and add the new source and licence to the media list below. The `object-fit: cover` rule crops images to fit; check the result after replacement.
4. **Change a navigation link:** in the header, change `<a href="#menu">Products / Services</a>` to point to an existing section such as `<a href="#contact">Contact</a>`. The value after `#` must match an actual section `id`. To rename a section target instead, update its `id` and every link that points to it.

## 7. Media sources and licences

Five photographs were downloaded from Pexels and resized/compressed through Pexels image delivery. Pexels permits free use and modification under the [Pexels License](https://www.pexels.com/license/), subject to its restrictions; attribution is not required but is provided here. Photographs illustrate the fictional brand and do not depict the restaurant itself.

| Local file | Creator and source |
|---|---|
| `images/fire.jpg` | Alexandra Kollstrem, [The Interior of a Restaurant](https://www.pexels.com/photo/the-interior-of-a-restaurant-8856579/) |
| `images/room.jpg` | Daniil Kondrashin, [Cozy Restaurant Table with Candlelit Ambiance](https://www.pexels.com/photo/cozy-restaurant-table-with-candlelit-ambiance-30420679/) |
| `images/rice.jpg` | Eva Bronzini, [Close-up of Dish in Plate on Table](https://www.pexels.com/photo/close-up-of-dish-in-plate-on-table-6216844/) |
| `images/grill.jpg` | Cristian Mihaila, [Fried Fish and Grilled Vegetables](https://www.pexels.com/photo/fried-fish-and-grilled-vegetables-11653557/) |
| `images/sweet.jpg` | Sylwester Ficek, [Elegant Dessert: Poached Pear with Honey and Spices](https://www.pexels.com/photo/elegant-dessert-poached-pear-with-honey-and-spices-34535224/) |

**Video:** Lokk1y, [Cooking Plov](https://commons.wikimedia.org/wiki/File:Cooking_Plov.webm), [Creative Commons Attribution–ShareAlike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/). The original video file is included unchanged. It shows pilaf being cooked and is presented as a general cooking film, not footage of Ember & Oak. If you adapt the video, follow the licence's attribution and share-alike conditions.

The stars, circles, lines and arrow marks are text/CSS graphics; no separate icon library is used.
