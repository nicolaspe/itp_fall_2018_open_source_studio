# Final Project Documentation
This is the documentation of the project [**Tracking of p5.js Spanish website translation and development of a translation guide (for any language)**](https://github.com/guillemontecinos/itp_fall_2018_open_source_studio/blob/master/final_project/proposal.md), developed for the class [**Open Source Studio**](https://github.com/Open-Source-Studio-at-ITP/) @ NYU ITP, Fall 2018.

## Week 1
### Week 1 Goals
* Track, translation and correction of Spanish p5.js website
* Track, translation and correction of Spanish p5.js reference (1/2)

### Advances
#### [Forking p5.js website repo](https://github.com/guillemontecinos/p5.js-website) to my GitHub account
The [original repo](https://github.com/processing/p5.js-website) was forked to my account and cloned into my local.

#### Translation Check
Translation check by page and handlers. Not mentioned handlers con be considered as ok.
##### Inicio: *p5js.org/es/*
* p1x2: modified
##### Descargar *p5js.org/es/download*
* editor-includes: translation is ok @ [es.yml](https://github.com/processing/p5.js-website/src/data/es.yml) but is not being shown in rendering process. Submitted in the following [Issue](https://github.com/processing/p5.js-website/issues/287)
##### Empezar *p5js.org/es/get-started/*
* download4: the word *miniaturizada* was changed for *reducida* due to the first one is not as common for this purpose.
* envirnoment9: modified
* envirnoment11: modified
* your-first-sketch2: modified
* **[Using p5 with a screen reader](https://p5js.org/es/learn/p5-screen-reader.html) page is not translated yet.**
* your-first-sketch9: modified
* your-first-sketch10: modified
* your-first-sketch12: modified

#### [Commit November 12th, 2018](https://github.com/guillemontecinos/p5.js-website/commit/c01572279342265c4f03fcfd9894f710fb86672f)
The above [Translations Check](https://github.com/guillemontecinos/itp_fall_2018_open_source_studio/blob/master/final_project/documentation.md#translation-check) were committed to my repo's fork and pulled to the Processing repo by the [Pull Request](https://github.com/processing/p5.js-website/pull/288).

##### Bibliotecas *https://p5js.org/es/libraries/*

* **[Link to p5.dom library](https://p5js.org/es/reference/#/libraries/p5.dom) is not translated yet.**
* **[Link to p5.sound library](https://p5js.org/es/reference/#/libraries/p5.sound) is not translated yet.**
* **[Link to p5.accessibility](https://github.com/processing/p5.accessibility) goes to a github .md file in English.**
* Note: Contributed libraries links were not reviewed.
* using-a-library1: modified
* using-a-library2: modified
* create-your-own1: modified

##### Aprender *https://p5js.org/es/learn/*
* learn1: modified
* **[Link to p5.js overview](https://github.com/processing/p5.js/wiki/p5.js-overview) goes to p5.js wiki @ Github. Not translated yet.**
* **[Link to Processing transition](https://github.com/processing/p5.js/wiki/Processing-transition) goes to p5.js wiki @ Github. Not translated yet.**
* **[Link to Local Server](https://github.com/processing/p5.js/wiki/Local-server) goes to p5.js wiki @ Github. Not translated yet.**
* **[Link to Using p5 with a screen reader](https://p5js.org/es/learn/p5-screen-reader.html) page is not translated yet.**
* **[Link to node.js and socket.io](https://github.com/processing/p5.js/wiki/p5.js,-node.js,-socket.io) goes to p5.js wiki @ Github. Not translated yet.**
* **[Link to Beyond the canvas](https://github.com/processing/p5.js/wiki/Beyond-the-canvas) goes to p5.js wiki @ Github. Not translated yet.**
* **[Link to Getting started with WebGL in p5](https://github.com/processing/p5.js/wiki/Getting-started-with-WebGL-in-p5) goes to p5.js wiki @ Github. Not translated yet.**

###### Color *https://p5js.org/es/learn/color.html*
Sub-page Color was modified.
* On [src/templates/pages/learn/color.hbs](https://github.com/guillemontecinos/p5.js-website/blob/master/src/templates/pages/learn/color.hbs) title and slug were modified from *learn* to *color*.
* On [es.yml](https://github.com/guillemontecinos/p5.js-website/src/data/es.yml) and [en.yml](https://github.com/guillemontecinos/p5.js-website/src/data/en.yml) a class for color and handlers were added at line 430.
* TODO: I'm changing color.hbs text to handlers. First I create them in the en.yml and then I copy them to es.yml and then translate. I'm at color-p2x4.

## Week 2
### Week 2 Goals
* Track, translation and correction of Spanish p5.js reference (2/2)
### Advances - Translation
###### Color *https://p5js.org/es/learn/color.html*
* Handlers in color.hbs were created and moved to the files en.yml, es.yml and zh-Hans.yml.
* Every handler at the es.yml were translated to Spanish.
###### Coordinate System and Shapes *https://p5js.org/es/learn/coordinate-system-and-shapes.html*
* Handlers in coordinate-system-and-shapes.hbs were created and moved to the files en.yml, es.yml and zh-Hans.yml.
* Every handler at the es.yml were translated to Spanish.

#### [Commit November 20th, 2018](https://github.com/guillemontecinos/p5.js-website/commit/3272d0c4de19af18339f0397989ed9cf22d9f135)
The above was committed to the source branch through the following [PR](https://github.com/processing/p5.js-website/pull/293).

## Week 3
### Week 3 Goals
* Track, translation and correction of Spanish p5.js examples (1/2)
### Advances - Fixing problems
Due to the PR [#293](https://github.com/processing/p5.js-website/pull/293) a bunch of problems were introduced to the website, because after that it couldn't be [compiled](https://github.com/processing/p5.js-website/commit/733e64f50cd196c2c41903617a1392faaf5f78bc#r31435805) again.

The errors introduced had two origins:

#### 1. YAML files can break compilation
The `.yml` files can break the page compilation process under syntax issues as double quotes within the text. Each YAML handler must be written as `color-rgb-title: "Color RGB"`, which means that the handler `color-rgb-title` has assigned the content `"Color RGB"` in the current language `.yml` file.

In some cases, the text translated from the original `.hbs` file (written in HTML) included double quotes used for highlight some idea. In those cases I didn't use the scape command `\` before the quotes, which was interpreted by the compiler as there was a syntax error due the handler finished more the one time.

#### 2. Handlers managing and new slugs creation at hbs files
The structure of `.hbs` files contains at the head a slot for declaring the folder where the page will be placed when compiled.

```
---
title: learn
slug: learn/
---
```

For nested pages -for example `p5js.org/es/learn/color.html`- the slug of the `.hbs` document must match the upper folder, in this case `learn`. This is directly related with the way handlers are displayed in the `.yml` file. For example, all the handlers for the `learn` page are written under its slug with a tab as follows:

```
learn:
  learn-title: "Aprender"
  learn1: "Estos tutoriales proveen una revisión en mayor profundidad o paso a paso sobre temas particulares. Revisa la "
```

For the case of nested pages it's important to not create a new slug for each page, because it can make the `.hbs` files not to find the handlers when calling the `i18n` data. So for the page color **it is not needed to create a new** `slug: color/` like:

```
color:
  color-title: "Color"
```

Instead of this, the color-related handler must be added to the `learn` list of handlers, as done in the PR [#297](https://github.com/processing/p5.js-website/pull/297).

### Results
* After the above the page can be created successfully.
* Creation of [translating.md](https://github.com/guillemontecinos/itp_fall_2018_open_source_studio/blob/master/final_project/translating.md).

## Week 4
### Week 4 Goals
* Track, translation and correction of Spanish p5.js examples (2/2)
* Write TRANSLATION.md (1/2)

## Week 5
### Week 5 Goals
* Write TRANSLATION.md (2/2)
* Final documentation
