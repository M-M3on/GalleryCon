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

- **Top bar**, always in sight while scrolling: text search, **Categories** (blue) and
  **Specifications** (green) buttons opening their panels (closed by a click outside), statistics
  and card scale. The active filters (and the text search) show as chips in a strip stuck under
  the bar, with the number of folders and images left: click a chip to remove it.
- Search by technical specification: lengths compared in metres, origin and user countries.
- Image viewer with thumbnails and the specifications of the folder.
- **Edit mode** (Menu): delete, rename folders or change their category, add or delete images,
  edit the specifications and create your own specification groups (name / value / unit lines).
- **Add a folder**: when a folder of the import already exists in the gallery (same categories and
  same name), a window lets you choose to merge it (its missing images are added) or to leave it
  unchanged.
- **Settings** (Menu, always available): card size, *Fit to window* and specifications panel of
  the viewer at opening, specification criteria shown at opening (including the ones you add by
  hand; the values typed are never saved), bottom banner and data file sizes. **Use the current
  view** copies what is on screen; **Save settings** downloads `gc_config.js`. The scale and viewer
  controls only change the current view.
- **Bottom banner**: in edit mode, type a text in the white banner at the bottom of the page and
  pick its color (or set it in Settings). As soon as it holds a text, it stays shown (bold,
  centered) on every page; empty, it disappears. It is saved in `gc_config.js`.
- Built-in help (**Help** button).

## Saving the gallery

A browser cannot write to your disk, so **Menu → Save changes** lists the modified files to
download. Copy them into the `data` folder next to `GalleryCon.html`, replacing the old ones:

```
GalleryCon/
├── GalleryCon.html
└── data/
    ├── gc_config.js           settings (optional: without it, the defaults apply)
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
  "odinUrl": "https://…",
  "Armament": [
    { "name": "Main gun", "value": "120", "units": "mm" },
    { "name": "Machine gun", "value": "12.7", "units": "mm" }
  ]
}
```

- `origin` and `proliferation` feed the country filters.
- Any other key holding a list of `{ name, value, units }` lines (like `Armament` above) is a
  custom group: shown under its own title, editable in GalleryCon and searchable.
- `dimensions`: one entry per value. Values are text (`"9.87"`, `"25 cm"`); `"INA"` or ranges are
  shown but not searchable. Lengths need a unit (mm, cm, m, km, in, ft, yd) to be searchable.
- Specifications edited in GalleryCon are saved in `data/gc_specifications.js`, never in your
  `specifications.json`.

## License

GalleryCon is free software, released under the
[GNU General Public License v3.0](https://www.gnu.org/licenses/gpl-3.0.html).

Contact: [github.com/M-M3on](https://github.com/M-M3on/)
