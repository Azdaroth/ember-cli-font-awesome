# ember-cli-font-awesome

An ember-cli addon for using Font Awesome icons in Ember applications.

This addon:

* Registers a Handlebars helper for rendering Font Awesome icon markup.
* Imports FontAwesome CSS and fonts into your app. (This can be disabled if necessary, see below.)

## Install in ember-cli application

For the sake of clarity: this is an [ember-cli](http://www.ember-cli.com) addon, not a standalone module.

```
# In your application's directory:
npm install --save-dev ember-cli-font-awesome
```

This addon works with ember-cli v0.0.43 and later.

## Basic usage

In your Handlebars templates:

```
{{fa-icon "camera"}}
```

If you prefer, you can use the `fa-` prefix in the icon name.

```
{{!-- Equivalent --}}
{{fa-icon "fa-camera"}}
{{fa-icon "camera"}}
```

[Complete list of Font Awesome icons](http://fortawesome.github.io/Font-Awesome/icons/)

You can also bind the icon name to a controller or model property:

```
{{fa-icon iconName}}
{{fa-icon menu.copyIcon}}
```

## Options

The [Font Awesome examples](http://fortawesome.github.io/Font-Awesome/examples/) illustrate the various options and their effects. It should be obvious how these options map to their `fa-icon` counterparts.

### Different icon sizes (changed in v0.0.4)

```
{{fa-icon "star" size="lg"}}
{{fa-icon "star" size=2}}
{{fa-icon "star" size=3}}
{{fa-icon "star" size=4}}
{{fa-icon "star" size=5}}
```

The old icon size syntax is deprecated, but still supported, as of v0.0.4.

### Rotate

```
{{fa-icon "camera" rotate=90}}
{{fa-icon "camera" rotate=180}}
{{fa-icon "camera" rotate=270}}
```

### Flip

```
{{fa-icon "bicycle" flip="horizontal"}}
{{fa-icon "car" flip="vertical"}}
```

### Spin

```
{{!-- using a boolean literal --}}
{{fa-icon "refresh" spin=true}}
{{!-- or a property --}}
{{fa-icon "refresh" spin=isLoading}}
```

### List icons

```
<ul class="fa-ul">
  <li>
    {{fa-icon "star" listItem=true}} Item
  </li>
</ul>
```

### Fixed width icons

```
<div class="list-group">
  <a class="list-group-item" href="#">
    {{fa-icon "home" fixedWidth=true}} Home
  </a>
  <a class="list-group-item" href="#">
    {{fa-icon "book" fixedWidth=true}} Library
  </a>
</div>
```

### Bordered & pulled icons

```
<p>
{{fa-icon "quote-left" pull="left" border=true}}
...tomorrow we will run faster, stretch out our arms farther...
And then one fine morning— So we beat on, boats against the
current, borne back ceaselessly into the past.
</p>
```

### Custom class names (new in v0.0.4)

```
{{fa-icon "bicycle" classNames="my-custom-class"}}
{{!-- results in: --}}
<i class="fa fa-bicycle my-custom-class"></i>
```

### Title attribute (new in v0.0.4)

```
{{fa-icon "edit" title="Edit the item"}}
{{!-- results in: --}}
<i class="fa fa-edit" title="Edit the item"></i>
```

## How do I prevent the addon from including Font Awesome assets?

Pass this option to the `EmberApp` constructor in your application's `Brocfile.js`:

```
var app = new EmberApp({
  emberCliFontAwesome: { includeFontAwesomeAssets: false }
});
```

The CSS and font files will then not be included in your app. Managing the Font Awesome assets yourself is what I would recommend doing for production apps. See the note below on how to do this with Bower. This addon includes the Font Awesome assets by default mainly for a better out-of-the-box experience.

## Including Font Awesome in your app using Bower

This should be straightforward for anyone familiar with ember-cli's handling of front-end dependencies through Bower.

```
# From your application's directory
bower install --save font-awesome
```

Then in your `Brocfile.js`:

```
/*
  This example is more verbose than necessary for the sake of illustration.
  You could, for example, include the Font Awesome assets as a Broccoli tree.
*/
app.import("bower_components/font-awesome/css/font-awesome.css");
app.import("bower_components/font-awesome/fonts/fontawesome-webfont.eot", { destDir: "fonts" });
app.import("bower_components/font-awesome/fonts/fontawesome-webfont.svg", { destDir: "fonts" });
app.import("bower_components/font-awesome/fonts/fontawesome-webfont.ttf", { destDir: "fonts" });
app.import("bower_components/font-awesome/fonts/fontawesome-webfont.woff", { destDir: "fonts" });
app.import("bower_components/font-awesome/fonts/FontAwesome.otf", { destDir: "fonts" });
```

## License

Public Domain
