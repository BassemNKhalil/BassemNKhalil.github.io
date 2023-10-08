## Welcome additions to a vanilla SPFx Components

- To scaffold using `yo @microsoft/sharepoint`, use the following command (then npm i) to ensure structure is correct before installing dependencies
`
yo @microsoft/sharepoint --solution-name "VanillaSolution" --framework "react" --component-type "webpart" --component-name "VanillaWebPart1" --skip-install
`

- The solution name is for the parent folder and the component name is for the WebPart component. This ensures the baseWebPart is `VanillaWebPart1WebPart.ts`, the WebPart under `components` is `VanillaWebPart1.tsx` and the package name is `vanilla-for-node.sppkg` in the `package-solution.json`

- Use the following command (removing `--solution-name "VanillaSolution"`) when adding a second WebPart to an existing solution. Make sure you're inside the solution folder.
`
yo @microsoft/sharepoint --framework "react" --component-type "webpart" --component-name "VanillaWebPart2" --skip-install
`

For more details, run `yo @microsoft/sharepoint --help` as per [yo options on MS Docs](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/toolchain/scaffolding-projects-using-yeoman-sharepoint-generator#command-line-options)

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
