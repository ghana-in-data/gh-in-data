# Ghana In Data

The Ghana in Data project is an open source project to creatively present data about Ghana with a focus on Sustainable Development Goals. We are a community of data enthusiasts, developers, designers, researchers, journalists, policy makers, and citizens who are passionate about data and its potential to drive positive change in Ghana.

The project is inspired by the [Our World In Data](www.ourworldindata.org) open source project and the [Ghana Open Data Initiative](www.data.gov.gh).

## Contributing

The Project is currently in its early stages and we are looking for contributors to help us build the platform. If you are interested in contributing, please read our [Contributing Guidelines](CONTRIBUTING.md).

## Current Repo Structure

[![Actions Status](https://github.com/ghana-in-data/gh-in-data/workflows/Continuous%20Integration/badge.svg)](https://github.com/ghana-in-data/gh-in-data/actions)
[![Test coverage](https://owid.github.io/badges/coverage.svg)](https://owid.github.io/coverage/)
[![Storybook](https://raw.githubusercontent.com/storybookjs/brand/master/badge/badge-storybook.svg)](https://owid.github.io/stories/)

The repo we use at [Ghana In Data](https://ourworldindata.org) to create and publish embeddable, interactive visualizations like this one:
https://github.com/ghana-in-data
[![A Grapher chart showing world-wide life expectancy at birth. Click for interactive.](https://ourworldindata.org/grapher/exports/life-expectancy.svg)](https://ourworldindata.org/grapher/life-expectancy)


## ✋ Disclaimer

This repo is currently is early in it's stage an it's not well-designed for reuse as a visualization library, nor for reproducing the full production environment, we are working to make as our tools less tightly coupled with our database structure. You are very welcome to make [contributions](CONTRIBUTING.md) to help us make this project better!


## 🏎 Getting started

To quickly get a version of the site running for developing Grapher features, we recommend following the [local development setup](docs/docker-compose-mysql.md) guide.

[Additional setup options](docs/setup-options-overview.md) are also available for other use cases.

## 🗂 Overview

Multiple projects are maintained in this repo:

### [Grapher](packages/%40ourworldindata/grapher/)

A client-side interactive data visualization library used by almost every chart on Our World in Data.

All grapher data is stored in a MySQL database that contains both JSON configuration objects for individual charts as well as the data values that they ingest.

The original Grapher project is built with [Lerna](https://github.com/lerna/lerna/) and [tsup](https://github.com/egoist/tsup).

### [Explorer](explorer/)

A Grapher-based tool that creates more complex [data visualization user interfaces](https://ourworldindata.org/explorers/migration).

Each explorer can be configured via a [panel](explorerAdminServer/) in the admin client. Their config files are stored in [a separate repository](https://github.com/owid/owid-content/tree/master/explorers).

### Grapher Admin

-   A [client-side](adminSiteClient/) project that provides a user interface for configuring graphers, explorers, and managing and uploading data.

-   A [server-side](adminSiteServer/) project that manages the MySQL database used by graphers.

### [Baker](baker/)

A [PM2](https://github.com/Unitech/pm2) project that builds a static copy of the Our World in Data website by merging the content authored in Gdocs with the grapher charts created in Grapher Admin.

### [Site](site/)

The React code for rendering our content in pages, used by the Grapher Admin and Baker.

## Tooling

Much of our code is based around [reactive programming](https://en.wikipedia.org/wiki/Reactive_programming) using [React](https://reactjs.org/) and [Mobx](http://github.com/mobxjs/mobx).

All code is written in [TypeScript](https://www.typescriptlang.org/).

If you want to enable pre-commit hooks, run `yarn husky`.

[Visual Studio Code](https://code.visualstudio.com/) is recommended for autocompletion and other awesome editor analysis features enabled by static typing.

## Why are we choosing to build on the oriinal owid project?

When the idea came to build a data visualisation tool for the Ghana in data project, we had to decide whether to build a new tool from scratch or to build on an existing tool. We decided to build on the original Our World in Data project for the following reasons:
> The owid-grapher solves this problem by using a single visualization codebase and crucially a single database into which all of our data is placed. Once the data has been imported, the process of creating a visualization is reduced to simply choosing what kind of visualization is needed and then selecting the relevant variables in the Grapher user interface. The result may then be customized, and is published to the web with the press of a button.
>
> Building on owid's work has very important advantages:
>
> -  **Integration with our global development database**: database of global development metrics can be integrated into visualization tool so that when we add and update empirical data the visualizations are all updated. (In contrast to this, a pre-existing tool would make the exploration of a database impossible and would require the preparation of each dataset separately for each visualisation.)

> -  **Flexibility**: We can leverage automation to change our entire system all at once. For example, if we decide we want to use a different source referencing style, we could easily update this across hundreds of charts. This makes it possible to scale our publication and to sustainably improve our work without starting from scratch at each round.
> -  **Risk mitigation**: We hope(!) that Our World in Data is a long-term project and we want the visualizations we produce to continue to be useful and available years from now. An external web service may be shut down or change for reasons we cannot control. We have had this experience in the past and learned our lesson from it.

> -  **Keeping everything up-to-date**: Because we want to be a useful resource for some time we make sure that we have a technology in place that allows us to keep all of our work up-to-date without starting from scratch each time. We have our global development database directly integrated in the Grapher and as soon as new data becomes available (for example from a UN agency) we can run a script that pulls in that data and updates all the visualizations that present that data.

---

Cross-browser testing provided by <a href="https://www.browserstack.com"><img src="https://3fxtqy18kygf3on3bu39kh93-wpengine.netdna-ssl.com/wp-content/themes/browserstack/img/bs-logo.svg" /> BrowserStack</a>

Client-side bug tracking provided by <a href="http://www.bugsnag.com/"><img width="110" src="https://images.typeform.com/images/QKuaAssrFCq7/image/default" /></a>
