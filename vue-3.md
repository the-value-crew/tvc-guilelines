## Introduction

This guide contains useful tips for developing Vue-3 projects.

## Preferred tools and packages

IDE: [Vs Code](https://code.visualstudio.com)

Vscode extensions: [Volar](https://marketplace.visualstudio.com/items?itemName=johnsoncodehk.volar)

Http client: [axios](https://github.com/axios/axios)

Toast notification: [vue-toastification](https://github.com/Maronato/vue-toastification)

Date/time package: [momentJS](https://momentjs.com/docs/), [dayjs](https://day.js.org/)

UI library: [Flowbite(tailwind css)](https://flowbite.com/)

For more please visit [tvc-productivity](https://github.com/the-value-crew/tvc-productivity#vscode-extensions), [tvc-javascript](https://github.com/the-value-crew/tvc-javascript).

## First and foremost

- Keep it simple
- Keep it organized
- Take advantage of framework features rather than inventing your own.

### Separate components into core & derived.

**Core** - Single-purpose, independent components.

**Derived** - Built using core components, probably mixing multiple core components. It may also act as a wrapper around core components adding custom functionalities.

### Store pages on different folder

Pages are also components but they are kept in a separate folder. A page contains core & derived components. Styles/css are kept in pages. Components aren’t tied to specific styling unless necessary.

### Pinia store

Pinia is used as Vue-3 store (not vuex). Each page has a dedicated **store**. Pages with many components with complex data & event flows make use of shared **store**. 

### Error handling

Api level error handling is done inside interceptors based on HTTP status. Application level error handling is done at specific components.

### Vue plugins

Vue plugins are used extensively to add custom functionalities. Rule of thumb: if a feature is required in more than one component/page, it's moved to plugin. Plugin may contain global variables, global methods. For application level $constants, icons, utils etc. plugin is used.

### Utils

Complex/redundant logic are moved to utils folder inside respective file.

### Naming convention

- Components are always named in CamelCase.
- While using, a <Component> camelcase is used so that filename and template tags look similar because the **human brain likes symmetry**.
- Component props & events are in lower camel case
- Events are always handled with an **eventHandlerFunc() s**o it can be differentiated from normal methods.
- Folders are named in small camelcase
- Css class and ids are named in kebab-case. Similar to tailwind.
- Use meaningful variable and method names. If it's long, feel free to use acronyms but make sure to include it on readme.

### Others

- Frequently used components are registered globally but keep in mind that these components aren’t removed from build during tree-shaking even if they aren’t used anywhere.
- CSS inside components are always scoped unless necessary.
- All async functions are executed with **async/await** inside try/catch block
