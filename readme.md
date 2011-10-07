jQuery dice plugin
==================

Very simple plugin which allows to display a dice, click on it and retrieve
a random number (between 1 and 6, of course.)

The dice glyphs can be replaced.

## Usage

As with all jQuery Plugins, you need to insert the plugin's javscript source
after jQuery itself. Additonally, the dice.gif must be copied to a web-reachable
path.

To create a dice and get it's value you need an empty div container and a
callback function that expects one argument. Than anywhere in your Javascript
Code you can just call:

    $('#diceContainer').dice({
      'glyphSrc': '/path/to/dice.gif',
      'callback': callbackFunction
    });

The available configuration options are:

- `background`: CSS-readable color value, defaults to `#ffffff`.
- `callback`: Callback function, called on value change. Defaults to `null`.
- `glyphSize`: Size of a single glyph (Glyphs have to be squares). Defaults to `40`.
- `glyphSrc`: Source of glyph image, contains glyphs for all 6 sides of the dice. Defaults to `glyph.gif`.
- `juggleTimeout`: Duration of the juggling animation in milliseconds. Defaults to `300`.
- `number`: Initial number, defaults to `1`.
- `selectGlyph`: Function which is called to change the current glyph. See __Custom Glyphs__.

## Custom Glyphs

This plugin has been designed to allow custom dice glyphs. To replace the default
set with your own, you simply need to create an image containing six squares in
the following layout:

    1 | 2 | 3
    ---------
    6 | 5 | 4

If your glyphs are larger than 40 * 40 pixels, you need to adjust the `glyphSize`
option to your chosen size, otherwise you only need to set `glyphSrc` to your new
glyph image.

In the unlikely event that you cannot or don't want to chose the above order, you
also need to provide a `selectGlyph`-function of the following signature:

    void selectGlyph(unsinged int number);

This function will be called whenever a new glyph is to be selected and is
responsible for changing the CSS background-position to the new number's
position in the glyph set. To access the dice container, the variable `m_this`
can be used as jQuery context.
