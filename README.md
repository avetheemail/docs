# paySon docs

This is not the stock Mintlify Starter Kit. We run several separate documentation sites, and each one has its own logo and palette. This file explains how to work with them and which rules we follow.

## Sites

All sites live in `G:\paySon`, next to this folder.

| Site | Folder | Port | Command |
|---|---|---|---|
| Main | `docs` | 3000 | `npm run dev:docs` |
| XD Docs | `site-xd` | 3001 | `npm run dev:xd` |
| Hot-M Docs | `site-hot-m` | 3002 | `npm run dev:hot-m` |

## Running the sites

You need Node.js 20 or later. Run all commands from `G:\paySon`, where `package.json` lives.

Install dependencies once:

```bash
cd G:/paySon && npm install
```

Run one site:

```bash
npm run dev:xd
```

Run all sites at once (stop with `Ctrl+C`):

```bash
npm run dev:all
```

Check a site for broken links and config errors:

```bash
npm run validate:xd
```

## Our rules

- **One brand, one folder.** Mintlify allows one `docs.json` per site, so you can't set a logo or palette per tab or group. For a new brand, create a `site-<name>` folder with its own `docs.json`, `style.css`, `favicon.svg`, and `logo/`.
- **Colors** go in `docs.json`: `colors.primary`, `colors.light`, `colors.dark`, and `background.color`.
- **Gray palette** lives in `style.css`. Override `--gray-50 … --gray-950` in `R G B` format, without commas.
- **Font** is Inter (`fonts.family`). **Theme** is `mint`, with dark mode as the default.
- **Pages** must be added to `navigation`, or they won't appear in the menu.
- **Ports:** the main site uses 3000, and new sites take the next free port (3003, 3004, and so on).
- **Language:** all documentation is written in English.
- **Writing style:** second person, short sentences, headings in sentence case.

## Add a new site

1. Copy `site-xd` to `site-<name>`.
2. In `docs.json`, change `name`, `colors`, and `background`. In `style.css`, change the gray palette. Put your SVG files in `logo/`.
3. In `G:\paySon\package.json`, add `dev:<name>` and `validate:<name>`, then include `dev:<name>` in `dev:all`.

## Publishing

Install the Mintlify GitHub app from your [dashboard](https://dashboard.mintlify.com/settings/organization/github-app). Changes deploy to production automatically after you push to the default branch.

## Troubleshooting

- The site won't start: run `npx mint update`.
- A page returns 404: run from a folder with a valid `docs.json`, and make sure the page is listed in `navigation`.
