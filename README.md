*Project is not maintained right now. Please see the note at the end of this file.*

Introduction
============

This Android widget aims to provide a scalable way to display large images (like Metro maps, paintings) while keeping the memory consumption as low as possible.

The source image will be provided in TILES, so that all tiles combined create the full scale image.

Current features:

* Specify a image pattern to find the tiles
* Freely navigate through the image using a two dimensional scroll view
* Load required tiles on demand and non-blocking
* Zoom levels using multiple levels of tiles
* Panning, Pinching etc (multitouch gestures), work in progress

Planned features:

* A way to overlay icons or other widgets at fix points (similar to Google Maps), which should be useful for annotations

Example
=======
``` xml
<asia.ivity.android.tiledscrollview.TiledScrollView
        android:id="@+id/tiledScrollView"
        android:layout_width="fill_parent"
        android:layout_height="fill_parent"
        app:file_pattern="tiger400/crop_%col%_%row%.png"
        app:tile_height="100"
        app:tile_width="100"
        app:image_width="400"
        app:image_height="300"
        app:zoom_buttons="true"
        />
```
Attributes:

* file_pattern - specifies the pattern to find the files. Placeholders `%col%` and `%row%` are mandatory
* tile_height & tile_width - specify the tile dimensions. The widget should be able to handle non-fitting images (i.e. if the last tile is smaller then others tiles well)
* image_height & image_width - image dimensions to support abovementioned functions.
* zoom_buttons - whether to enable the zoom buttons, default is `true`.

The attributes are very likely to be reduced and cut. I prefer the widget to be more simple in the long term.

Multiple Zoom Levels
====================

The View supports different zoom levels. You can add them using Java.

``` java
final TiledScrollView tiledScrollView = (TiledScrollView) findViewById(R.id.tiledScrollView);

tiledScrollView.addConfigurationSet(TiledScrollView.ZoomLevel.LEVEL_1,
        new ConfigurationSet("tiger800/crop_%col%_%row%.png", 100, 100, 800, 600));

tiledScrollView.addConfigurationSet(TiledScrollView.ZoomLevel.LEVEL_2,
        new ConfigurationSet("tiger1600/crop_%col%_%row%.png", 100, 100, 1600, 1200));
```

Credits
=======

* Apple's iOS CATiledLayer for inspiring this work
* http://GORGES.us for developing and publishing a two dimensional ScrollView
* http://www.animalspedia.com/wallpaper/The-Siege---Siberian-Tiger/ for providing a nice sample picture

Apps using this library
=======================

* https://play.google.com/store/apps/details?id=asia.ivity.qifu.android.map
* Send a pull request to add your App.

Maven
=====

The plugin is available in the maven central repository.

``` xml
<dependency>
  <groupId>asia.ivity</groupId>
  <artifactId>tiledscrollview</artifactId>
  <version>1.1.1</version>
  <type>apklib</type>
</dependency>
```

License
=======

This library is released under a BSD license. See the LICENSE file included with the distribution for details.

Not for you?
============

Check out https://github.com/moagrius/TileView, which is a up to date Tiling library which includes many features.
