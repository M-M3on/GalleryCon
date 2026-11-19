# GalleryCon

An image gallery built from your folders, running entirely in your browser.
One HTML file, no server, no installation: your images never leave your computer.

## Getting started

1. Download `GalleryCon.html` and put it in a folder named `GalleryCon`.
2. Open it in your browser (Chrome, Edge, Firefox or Safari).
3. **Menu → Add a folder**, then pick the root of your image tree.

Each folder containing images becomes a card; its parent folders become categories.

```
My_collection/
├── Land/
│   └── Tanks/
│       └── Leclerc/
│           ├── specifications.json   (optional)
│           ├── photo001.jpg
│           └── photo002.jpg
└── Sea/
    └── ...
```

The selected folders are only read: GalleryCon never modifies them.

## Features

- Filters by category, text search, search by technical specification (lengths compared in
  metres, origin and user countries).
- Image viewer with thumbnails and the specifications of the folder.
- **Edit mode** (Menu): delete folders, change their category, add or delete images, edit the
  specifications.
- **Bottom banner**: in edit mode, type a text in the white banner at the bottom of the page and
  pick its color. As soon as it holds a text, it stays shown (bold, centered) on every page; empty,
  it disappears. It is saved with the gallery.
- Built-in help (**Help** button).

## Saving the gallery

A browser cannot write to your disk, so **Menu → Save changes** lists the modified files to
download. Copy them into the `data` folder next to `GalleryCon.html`, replacing the old ones:

```
GalleryCon/
├── GalleryCon.html
└── data/
    ├── gc_specifications.js   folders, categories, specifications and image index
    ├── gc_covers-01.js        first image of each folder (10 MB files)
    └── gc_images-01.js        other images (70 MB files)
```

Only the files that changed are listed. The images are loaded on demand, as you scroll or open
a folder, so large galleries stay fast.

**Export standalone HTML** (Menu) creates one single file containing everything, handy to share a
small gallery (a warning is shown above 50 MB). A standalone file always shows its own content and
ignores any `data` folder next to it.

## specifications.json

Optional, in a folder next to its images. Every field is optional:

```json
{
  "alternateDesignations": ["AMX-56"],
  "origin": ["France (FRA)"],
  "proliferation": ["France", "United Arab Emirates", "Jordan"],
  "dimensions": [
    { "name": "Length", "value": "9.87", "units": "m" },
    { "name": "Weight, Combat", "value": "56.5", "units": "t" }
  ],
  "odinUrl": "https://…"
}
```

- `origin` and `proliferation` feed the country filters.
- `dimensions`: one entry per value. Values are text (`"9.87"`, `"25 cm"`); `"INA"` or ranges are
  shown but not searchable. Lengths need a unit (mm, cm, m, km, in, ft, yd) to be searchable.
- Specifications edited in GalleryCon are saved in `data/gc_specifications.js`, never in your
  `specifications.json`.

## License

GalleryCon is free software, released under the
[GNU General Public License v3.0](https://www.gnu.org/licenses/gpl-3.0.html).

Contact: [github.com/M-M3on](https://github.com/M-M3on/)
