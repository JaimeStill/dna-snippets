# Change Log

All notable changes to the "dna-snippets" extension will be documented in this file.

Check [Keep a Changelog](http://keepachangelog.com/) for recommendations on how to structure this file.

## 0.0.9

**Added** new snippets as follows:  

* `dna.mat-route-tab` - HTML

**Modified**:  

* `dna.route` - TypeScript - Adjust to the convention that route components no longer use the `Component` segment of their name. For instance, `HomeComponent` should now be `HomeRoute` and should have the files `home.route.ts` and `home.route.html`.
* `dna.dialog` - TypeScript - Correct `import` statement for `MatDialogRef` and `MAT_DIALOG_DATA` to `@angular/material/dialog`.

## 0.0.8

Add missing backtick in README.

## 0.0.7

No changes beyond version number.

## 0.0.6

**Added** new snippets as follows:

* `dna.ent-dbset` - C#
* `dna.ent-keymap` - C#
* `dna.ext-base` - C#
* `dna.ext-query` - C#
* `dna.ctl-base` - C#
* `dna.ctl-query` - C#
* `dna.mat-select-change` - HTML
* `dna.api` - TypeScript
* `dna.source` - TypeScript

**Modified**:

* `dna.ent-class` - Remove all but `Id` as default property.
* `dna.sgl-hub` - Remove default `OnDisconnect` registration.
* `dna.card-shell` - Make all classes part of snippet parameter.
* `dna.flex-container` - Make class parameterized.
* `dna.async-container` - Parameterize `loading` template.
* `dna.loading-template` - Parameterize `loading` template reference variable.
* `dna.mat-select` - Remove `selectionChange` event binding.
* `dna.model` - Remove all but `id` as default property.
* `dna.service` - Update to reflect library layout and parameterize services / config directory paths.

## 0.0.5

**Added** new snippet as follows:

* `dna.ctl-get-routed` - C#  

> See updated [README](./readme.md) for details

## 0.0.4  

**Fixed**:

* `dna.dnd-route` - Missing quotations and comma in `@Component` metadata.

## 0.0.3

**Added** new snippets as follows:

* `dna.dnd-selector` - TypeScript
* `dna.dnd-selector` - HTML
* `dna.dnd-selector` - CSS

> See updated [README](./readme.md) for details

## 0.0.2  

**Added** new snippets as follows:  

* `dna.obs-input` - TypeScript
* `dna.idx-component` - TypeScript
* `dna.idx-dialog` - TypeScript
* `dna.idx-model` - TypeScript
* `dna.idx-pipe` - TypeScript
* `dna.idx-route` - TypeScript
* `dna.idx-child-route` - TypeScript
* `dna.idx-service` - TypeScript
* `dna.card-shell` - HTML
* `dna.flex-container` - HTML
* `dna.async-container` - HTML
* `dna.loading-template` - HTML
* `dna.searchbar` - HTML
* `dna.mat-select` - HTML
* `dna.mat-input` - HTML
* `dna.mat-input-trv` - HTML
* `dna.mat-textarea` - HTML
* `dna.mat-slider` - HTML
* `dna.mat-slide-toggle` - HTML
* `dna.mat-menu` - HTML
* `dna.mat-tab-nav` - HTML

> See updated [README](./readme.md) for details

## 0.0.1

* Initial release