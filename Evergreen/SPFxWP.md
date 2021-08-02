## Welcome additions to a vanilla SPFx Components

Create a new folder `VanillaWP`, cd into the new folder & scaffold using `yo @microsoft/sharepoint`

- Provide the name `Vanilla` for both solution and webpart - this ensures the baseWebPart is `VanillaWebPart.ts`, the webpart is `Vanilla.tsx` under `components` and the package name is `vanilla.sppkg`
- When unsure, use `--skip-instal` to make it quick and iterate
- The following hasn't been tested but may automate the above but not yet tested:

         yo @microsoft/sharepoint
         --solution-name "Vanilla"
         --framework "react"
         --component-type "webpart"
         --component-name "Vanilla"
         --skip-install
         --environment "spo"

  [yo options on MS Docs](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/toolchain/scaffolding-projects-using-yeoman-sharepoint-generator#command-line-options)

1. [version-sync](../posts/2021-05-19.md)
1. [spfx-fast-serve](https://github.com/s-KaiNet/spfx-fast-serve#how-to-use)
1. [Update baseWP to include all props by default](../minis/2021-06.md#mini-1-add-all-props-in-spfx-wp-by-default)
1. [Support theme variant (section backgrounds) - WebParts only](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/guidance/supporting-section-backgrounds)

- Align package title in `config\package-solution.json` which is shown in AppStore with the webpart title in `VanillaWebPart.manifest.json`
- Install [PnP Property controls](https://pnp.github.io/sp-dev-fx-property-controls/) and add [Property Editor](https://pnp.github.io/sp-dev-fx-property-controls/controls/PropertyPanePropertyEditor.html) and amend baseWebPart `VanillaWebPart.ts` with another group as below to edit all properties and show WebPart version

      {
         groupName: 'v' + this.context.manifest.version,
         groupFields: [
            PropertyPanePropertyEditor({
            webpart: this,
            key: 'propertyEditor',
            }),
         ],
      },

- Use single props class for both baseWebPart `VanillaWebPart.ts` and WebPart `Vanilla.tsx`
- Update spfx-fast-serve config under `fast-serve/webpack.extend.js`

      const webpackConfig = {
         devServer: {
         // open: 'chrome',
         open: false,
         openPage: "https://<tenant-name>.sharepoint.com/_layouts/15/workbench.aspx"
         }
      }

- Update icon (officeFabricIconFontName) under `VanillaWebPart.manifest.json` - use [OUI Fabric Icons site](https://uifabricicons.azurewebsites.net/) to browse for the right icon

### Useful additions - as needed

1. [PnP controls](https://pnp.github.io/sp-dev-fx-controls-react/)
   1. WebPart Title
   1. [Placeholder](https://pnp.github.io/sp-dev-fx-controls-react/controls/Placeholder)
   1. [Paging](https://pnp.github.io/sp-dev-fx-controls-react/controls/Pagination)
1. [PnP Property controls](https://pnp.github.io/sp-dev-fx-property-controls/)
   1. [Collection Data](https://pnp.github.io/sp-dev-fx-property-controls/controls/PropertyFieldCollectionData)
   1. [Property Editor](https://pnp.github.io/sp-dev-fx-property-controls/controls/PropertyPanePropertyEditor)
1. [Fluent UI Controls](https://developer.microsoft.com/en-us/fluentui#/controls/web)
   1. [Spinner](https://developer.microsoft.com/en-us/fluentui#/controls/web/spinner)
   1. Details List
