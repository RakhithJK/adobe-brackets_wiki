Brackets allows you to create editor themes that users can easily install and switch between. You can create a theme with simple CSS or LESS file and a package.json file with metadata for your theme.

Themes are simple Brackets extensions that can adjust the colors used in the editor area.

## Creating the Extension

* Open your extensions folder by selecting "Help > Show Extensions Folder" in Brackets
* Inside the `user` folder, create a new "yourThemeName" folder
* Inside the yourThemeName folder create package.json and theme.less files.

## package.json

The `package.json` file tells Brackets and, ultimately, the Extension Registry about your extension. Your theme's package.json should look something like this:

```javascript
{
    "name": "yourname.my-shiny-theme",
    "title": "My Shiny Theme",
    "description": "This theme is so shiny that you'll need to wear shades!",
    "homepage": "https://github.com/yourname/my-shiny-theme",
    "version": "1.0.0",
    "author": "Your Name <your@email> (http://your.url)",
    "license": "MIT",
    "theme": {
        "file": "theme.less",
        "dark": true
    },
    "keywords": ["theme"]
}
```

This seems like a lot, but giving all of this information will give potential users of your theme the most information in the Extension Manager.

The "theme" part is unique to themes and is the trigger that tells Brackets that this extension is a theme. The `file` property tells Brackets which file in your extension is the stylesheet for your theme. If your theme has a dark appearance, use the `dark` flag to tell Brackets that it should make other elements beyond the editor dark as well.

Read more about package.json on the [extension package format page](https://github.com/adobe/brackets/wiki/Extension-package-format#packagejson-format).

## Developing Your Theme

Brackets has a workflow that will help you iteratively create your theme. If you set up your theme files as suggested in the "Creating the Extension" section above, your new theme should be available for use right away.

* Start up Brackets
* Select your theme in the theme settings (`View > Themes...`)
* Drag your theme.less file into Brackets

Now, when you save changes to your theme.less file, your changed theme is automatically applied to Brackets.

## Theme Styles

The base theme is the "Brackets Light" theme and all of the styles that you add will be added to the page after the base theme.

For an up-to-date example of a complete theme, take a look [at the Brackets Dark theme](https://github.com/adobe/brackets/blob/master/src/extensions/default/DarkTheme/main.less).

Your theme's stylesheet is processed as a LESS file that is wrapped with `#editor-holder {`. Setting the main foreground and background colors looks like this:

```css
.CodeMirror, .CodeMirror-scroll {
    background-color: #1d1f21;
    color: #ddd;
}
```

To apply your color scheme to the editor area, LESS will convert this to:

```css
#editor-holder .CodeMirror, #editor-holder .CodeMirror-scroll {
    background-color: @background;
    color: @foreground;
}
```

Tips for creating your theme's CSS:

* Starting with an [existing theme]((https://github.com/adobe/brackets/blob/master/src/extensions/default/DarkTheme/main.less)) is always easier
* Use the Dev Tools element inspector (`Debug > Show Developer Tools`) to view the elements in the editor
* You can customize the styles within an inline code editor by adding `.inline-widget .CodeMirror` to your CSS selector
* Watch out for the colors that aren't displayed all the time:
    * matching brackets
    * matching tags in HTML
    * matches for the "Find" command
    * the highlight for the active line (`View > Hightlight Active Line`)

## What about other UI elements?

Brackets and other editors separate the notion of "editor themes" from that of "UI themes". Editor themes provide colors for the text editor area based on the syntax highlighting engine of the editor. UI themes can style the rest of the UI.

Editor themes have certain advantages. They are:

* simpler to create because they don't have very many things to style
* easier to test because you don't need to look through the whole UI to see the impact of changes
* less likely to break between Brackets releases, because the Brackets DOM can change at any time

As of release 0.42, Brackets *only* supports editor themes.

Inline editors other than inline code editors (for example, the inline color editor), are considered "UI" and should not be styled by editor themes.

## Publishing Your Theme

Congratulations! You've created a new theme. Now you can share it with the world:

* zip your theme's folder into a new zip file
* upload the zip file to the [extension registry](https://brackets-registry.aboutweb.com/)