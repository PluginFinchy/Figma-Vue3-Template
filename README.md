# Vue 3 Plugin Template for Figma

This template gets you up and running and building figma plugins with the Vue3 framework in a short time.

## Features:

- Vue
- Typescript
- [figma-plugin-ds](https://github.com/thomas-lowry/figma-plugin-ds) integration
- Message handler helper functions to simplify communication between the main code and the UI code. (Thanks to [@jackiecorn](https://github.com/jackiecorn))
- Live Server preview to make building UIs faster. `npm run preview`

This template is built on top of [@jackiecorn/Vue-Plugin-Template](https://github.com/jackiecorn/Vue-Plugin-Template) and updated to use Vue3
## Downloading the template

There are a few ways you can use this template. 

The simplest way is to hit ['use this template'](https://github.com/LukeFinch/Figma-Vue3-Template/generate) 

Or [download the .zip](https://github.com/LukeFinch/Figma-Vue3-Template/archive/main.zip) of this repo.

Alternatively you can use this template as a template for your own github repo through the [github cli](https://github.com/cli/cli)

`gh repo create "<YOUR REPO NAME>" -p "https://github.com/LukeFinch/Figma-Vue3-Template"`


## How to use?

1. Install dependencies with `npm i`.
2. Run `npm run dev` and a folder named `dist` will be created.
3. In the Figma desktop app, click on **Create new plugin** / **Link existing plugin** and point it to the `manifest.json` in this project.
4. Now you can edit the main Figma code from `src/code.ts` and the UI code from `src/ui/ui.vue`. Hitting save will auto-reload the build so you can see your changes right away.
5. When you're ready to publish the plugin, run `npm run build` to create a production build.

## Message handlers

To communicate between the main code and the UI code, you can use the `dispatch` and `handleEvent` functions to send and listen to messages between the two environments.

Sending a message from the main code to UI code:

```
dispatch('eventName', data)
```

Handling messages from the UI code to the main code:

```
handleEvent('eventName', data => {
    // Do something with the data
})
```

Note that data is optional so you could simply send a message by `dispatch('eventName')`.

In the vue UI code, `dispatch` can be called anywhere, but `handleEvent` functions should be called in `mounted()` so they would only be called first and only once.

This project template shows an example of a UI button sending a message to the main code to create a rectangle node. The main code then sends back the created node ID to be displayed in the UI.
