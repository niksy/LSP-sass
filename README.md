# LSP-sass

Sass support for Sublime’s LSP.

Provided through [Some Sass language server](https://github.com/wkillerud/some-sass/tree/main/packages/language-server).

### Installation

* Install [LSP](https://packagecontrol.io/packages/LSP) and `LSP-sass` via Package Control.
* Restart Sublime.

### Configuration

There are some ways to configure the package and the language server.

- From `Preferences > Package Settings > LSP > Servers > LSP-sass`
- From the command palette `Preferences: LSP-sass Settings`

### FAQ

### Make Sass language server take priority over CSS language server

If you’re using both Sass and [CSS language server](https://github.com/sublimelsp/LSP-css),
CSS language server can take over priority over Sass so you can lose definition jump for variables.

You need to adjust CSS language server settings `priority_selector` so Sass language server has priority:

```json
{
	"priority_selector": "source.css - source.scss"
}
```

### Duplicate link and color definitions when using CSS language server

Since Sass language server augments CSS capabilities, there can be situations where you can get
duplicate definitions such as colors and links.

You need to disable those capabilities in CSS language server settings:

```json
{
	"disabled_capabilities": {
		"documentLinkProvider": true,
		"colorProvider": true
	}
}
```

If you’re using Volar, this also needs to be set inside language server settings for Volar, but beware
this sets those capabilities for all other languages such as JS and HTML so you may lose some capabilities
for those language servers.
