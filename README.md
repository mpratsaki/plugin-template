# Cider + Vue 3 + TypeScript + Vite

**(Requires Cider 4 or later)**

This is a template/boilerplate for creating Cider plugins using Vue 3, TypeScript, and Vite.

## Starting a new plugin project
Using **Node**
```bash
npx giget github:ciderapp/plugin-template your-plugin-name
```
Using **Bun**
```bash
bunx giget github:ciderapp/plugin-template your-plugin-name
```

## Available Commands
- `npm run dev` - Start development server, Cider can then listen to this server when you select "Enable Vite for Plugins" from the main menu
- `npm run build` - Build the plugin to `dist/`
- `npm run prepare-marketplace` - Prepare a ZIP package in the correct format for the Cider Marketplace

## Plugin configuration
Edit `src/plugin.config.ts`. The build generates `dist/plugin.yml` from it, so set your plugin's metadata there.

Cider 4 only runs a plugin if its default export has a `pluginKitVersion`. `definePluginContext` from the PluginKit version this template uses (`@ciderapp/pluginkit#cider-4`) adds it for you. If Cider logs `Plugin <identifier> does not specify a pluginKitVersion, cancelling loading.`, the plugin was built with an older PluginKit: update it with `pnpm run update-pluginkit`.

## How to install after build
1. In Cider, go to **Settings → Plugins**, open the **⋯** menu and choose **Open AppData folder**. This is the folder Cider reads extensions from (on Windows, `%APPDATA%\sh.cider.dotnet`).
2. Copy the contents of `dist/` into `plugins/<identifier>/` inside that folder, e.g. `plugins/org.username.plugin-template/`.
3. Back in **Settings → Plugins**, choose **Refresh plugins list** from the **⋯** menu. Your plugin shows up under **Disabled**: click it and enable it. Cider doesn't run newly installed plugins until you do.

## Preparing a ZIP package for the Cider Marketplace
Run `npm run prepare-marketplace`

Running this script will create a ZIP file in the `publish` directory that is ready to be uploaded to the Cider Marketplace.

To configure this plugin edit `src/plugin.config.ts`
