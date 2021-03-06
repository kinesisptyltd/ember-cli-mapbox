# Ember-cli-mapbox

Template driven Mapbox.js maps in Ember CLI.

## Installation

```
ember install ember-cli-mapbox
```

Add your access token to `config/environment.js`:

```js
mapbox: {
  accessToken: 'yourAccessToken',
},
```

## Components

### mapbox-map

The addon includes a component for constructing a mapbox map:

```hbs
{{mapbox-map mapId='ember-cli-mapbox.7c3914f2' divId='mega-map'}}
```

Which will generate a `<div id="mega-map">`, and initialise the map with the
corresponding mapId form mapbox.

If `divId` is not specified it defaults to 'map'.

You can specify the zoom level and center of the map as attributes

```hbs
{{mapbox-map
  mapId=model.sfMapId
  center=(mapbox-coords 37.768 -122.381)
  zoom=13}}
```

### mapbox-marker

When used as a block `mapbox-map` will yield an instance of the map. You can use
this to add markers to the map through the `mapbox-marker` component in your
templates:

```
{{#mapbox-map mapId='ember-cli-mapbox.7c3914f2' as |map|}}
  {{#each positions as |position|}}
    {{mapbox-marker map=map coordinates=position.coordinates}}
  {{/each}}
{{/mapbox-map}}
```

You can also specify the `size`, `color` and `sybol` of the marker with those
attributes and trigger an `onclick` event.

Popup titles can be set with `popup-title` and can be opened by setting the
`is-open` property to true.

## Helpers

### mapbox-coords

A helper for setting up a coordinate pair from a latitude and a longitude e.g.

```hbs
{{mapbox-map
  mapId=model.sfMapId
  center=(mapbox-coords 37.768 -122.381)
  zoom=13
  as |map|}}
```

or

```hbs
{{mapbox-marker map=map coordinates=(mapbox-coords 23.333, 45.422)}}
```

# Collaborating

If you want to collaborate on this Ember addon:

## Installation

* `git clone` this repository
* `npm install`
* `bower install`

## Running

The dummy app has some basic mapbox usage.

* `ember server`
* Visit your app at http://localhost:4200.

## Running Tests

* `ember test`
* `ember test --server`

## Building

* `ember build`

For more information on using ember-cli, visit [http://www.ember-cli.com/](http://www.ember-cli.com/).
