

# Changes in lattice 0.22

* TODO: data.frame methods


# Changes in lattice 0.21

* The color scheme used in the default graphical settings has been
  updated to use modern palettes, thanks to Achim Zeileis. It is also
  easier to customize the color palette in `standard.theme()`, via a
  new function `custom_theme()`.

* `panel.levelplot()` has a new `region.type = "countour"` argument
  allowing smooth region boundaries similar to `filled.contour()`.
  Based on code in the `gridGraphics` package by Zhijian (Jason) Wen
  and Paul Murrell, ported by Johan Larsson.
  
* Improved behaviour of `auto.key`, including better default placement
  and better handling of the `type` argument in scatterplots. Based on
  patch by Johan Larsson.
  
* Default values of `auto.key` and `grid` can now be set via `lattice.options()`.

* New `smooth` argument in `panel.xyplot()` as preferred alternative
  to using `type` to indicate type of smoothing desired.

* Vector argument support in `panel.violin()`. Contributed by Stefan
  Eng.
  
* Better handling of degenerate data in `panel.violin()`.

* New option to optimize some grid unit calculations via
  `lattice.options(optimize.grid = FALSE)`. Currently, setting this to
  `TRUE` may speed up some multi-page plots.

* New "grid" vignette containing examples of using raw grid with
  lattice. Contributed by Paul Murrell.

* New `fill` argument in `panel.3dscatter()`.

* Improved `call` component in trellis objects, fixing a longstanding
  [bug](https://stat.ethz.ch/pipermail/r-devel/2017-May/074243.html).

* `draw.key()` now considers title in width calculations.

* Miscellaneous bugfixes and improvements.


# Changes in lattice 0.20

* The primary goal of the 0.20 series is to further improve
  documentation, building up to an eventual 1.0 release.  Specific
  major changes are given below.

* Use `dev.hold()` / `dev.flush()` introduced in R 2.14.0 for smoother
  displays and transition.

* It is now easier to use raster images in levelplot() by specifying
  top-level argument 'useRaster=TRUE'.

* 'pos' can now be a vector in `ltext()`, just as it can in `text()`.

* Explicit components in 'colorkey' (for `levelplot()`) to specify
  graphical parameters of boundary and tick marks / labels.

* "spline" added as a possibly 'type' in `panel.xyplot()`, following a
  suggestion from Patrick Breheny.

* Support for traditional graphics-like log scale annotation, using
  `scales = list(equispaced.log = FALSE)`.

* `parallel()` deprecated in favour of `parallelplot()`, to avoid
  potential confusion with the parallel package.

* The internal lattice.status list is cleaned up whenever new page
  starts.  This should fix lattice bug #1629.

* New option to provide a custom rule for computing default
  breakpoints in `histogram()`. See ?histogram for details.

* New datasets `USMortality` and `USRegionalMortality`.

* Support for triangular ("open") endpoints in colorkey.

* Support for title in colorkey. Based on patch by Johan Larsson.

* Improved prepanel calculations for stacked barchart with missing
  values.



# Changes in lattice 0.19

* The primary goal of the 0.19 series is to improve documentation and
  fix some obscure but long-standing bugs, building up to an eventual
  1.0 release.  Specific major changes are given below.

* Added new arguments 'grid' and 'abline' in panel.xyplot().

* Added a "panel.background" setting.

* Restructured storage of plot-specific information, fixing bug
  reported in
  https://stat.ethz.ch/pipermail/r-help/2007-October/143567.html

* Added a CITATION file.

* Added a new "axis.text" setting. 

* Added the option to scale data inside panel.3dscatter() and
  panel.3dwire() rather than assuming ther are already scaled.  This
  may be helpful for use in user-written panel functions, with
  (additional) data specified in the original scale.

* 'varnames' can now be expressions in splom()/parallel().
 
* Added support for 'xlab.top' and 'ylab.right' arguments.

* Improved axis labelling in splom(), including support for date-time
  data.

* panel.pairs() now passes arguments i and j to (sub)panel and
  diag.panel functions.

* Default prepanel functions are now user-settable through
  lattice.options()

* par.[main|sub|xlab|ylab].text parameter settings are more powerful.

* Added support for 'just' component in draw.key() to allow
  justification of legend placement.

* Graphical arguments in panel.superpose can now be lists.

* Added support for raster colorkeys.

* Added new 'height' component for keys.

* Improved vectorization of graphical parameters in panel.bwplot.

* Expanded trellis.grobname() and used it to provide a name for all grobs.

* New panel.spline() function.

## Bug fixes

* More realistic check for equispaced grid in
  panel.levelplot.raster().

* Improved partial matching of component names in 'key' and 'scales'.

* xyplot.ts() now allows graphical parameters to be given as vectors 
  (inside a list) for each series. Passes lists to panel.superpose.

* panel.axis() now does NOT draw tick marks if 'ticks = FALSE'.


# Changes in lattice 0.18

* Hosting of the upstream sources has moved to R-forge.  This allows,
  among other things, the use of the R-forge issue tracker.

* New xyplot.ts method, merging versions previously available
  in latticeExtra and zoo (thanks to the efforts of Felix Andrews)

* An argument 'group.value', containing the level of the group, is now
  passed by panel.superpose to the 'panel.groups' function

* Specifying 'auto.key' as a list now produces a legend even in the
  absence of 'groups', provided a 'text' component has been included

* The 'layout' argument now accepts NA for number of columns or rows.

* Scale limits 'xlim' & 'ylim' can have one NA to fix only one side.

* Date and POSIXt scales now use new methods to calculate axis ticks,
  and now respond to the 'tick.number' component of 'scales'.

* 'panel.qqmath' gains an argument 'tails.n' for exact data on tails.


# Changes in lattice 0.17

## New features

* New function simpleTheme() for creating nested lists without
  specifying the nesting structure (which is guessed)

* Support for lattice.option(print.function) which is the function
  actually used when print.trellis() is called

* New argument 'box.width' wherever 'box.ratio' is available (e.g.,
  panel.bwplot, panel.barchart, etc.), to specify absolute thickness
  (of boxes, bars, etc.)

* New panel.refline() function, same as panel.abline(), but with
  default parameters from the "reference.line" settings.

* parallel() has a new 'horizontal.axis' argument; when FALSE, the
  axes are vertical and are stacked side by side.

* densityplot() now supports weights.

* dotplot.table() etc. allow change of orientation (horizontal=FALSE).

* New function panel.identify.cloud() to interactively label
  three-dimensional scatterplots.

* Added support for notches in panel.bwplot (based on patch from Mike
  Kay)

* New panel function panel.smoothScatter (relocated from Bioconductor
  package geneplotter)

* Added German translations (contributed by Chris Leick)

* reordered documentation to make PDF manual more readable

## Bug fixes

* Make translations available (they were never actually installed before)


# Changes in lattice 0.16

## Changes in behaviour

* 'x' in dotplot(~x, data) etc now gets names(x) set to
  rownames(data).  Update: this feature has now been removed, as the
  resulting behaviour is undesirable for bwplot()

* the 'call' component of a "trellis" object is set to a better value
  than before (at least for the methods in lattice).  One consequence
  is that update.default() now works for cases in which
  update.trellis() doesn't (i.e. those where data packets need to
  change)

* barchart.table now has an 'horizontal' argument

* levelplot.matrix() now allows specification of column labels or
  positions through arguments 'row.values' and 'column.values'

* width calculation for rectangles changed for levelplot() when 'x',
  'y' are factors; they are set to 1, rather than trying to
  accomodate unequally spaced 'x' and 'y' values.  This is important
  when there are empty levels

* dimnames() of a "trellis" object is now settable (this allows
  changing names and levels of conditioning variables)

* labels ('xlab', 'main', etc) can now be character vectors.  In
  their list form, they support more graphical parameters as well as
  finer positioning (justification, rotation, etc.)

* 'strip.left' gets called with 'horizontal = FALSE', so
  'strip.left = strip.default' now works as expected


# Changes in lattice 0.15

## New features

* Default panel functions are now settable options

* Limits of a parallel coordinates plot can now be controlled via
  functions

* New 'panel.aspect' argument for cloud and wireframe

* Better support for factors in cloud and wireframe

* More flexible placement of legends with x, y and corner.  In
  particular, corner can have fractional values, and (x, y) can refer
  to a position w.r.t. two potential bounding boxes depending on
  lattice.getOption("legend.bbox") ('full', meaning full plot region,
  or 'panel', meaning the subregion containing panels and strips.
  The default is 'panel', which is a change in behaiour)

* trellis.focus() now allows choosing panels interactively.

* New interaction functions panel.identify.qqmath() and
  panel.brush.splom()

* There is now an error handling mechanism for panel functions.  By
  default, errors in panel functions no longer stop execution.  See
  ?print.trellis for details.

* Note: Some of these are also available in updated 0.14 versions


## Changes in behaviour

* non-numeric data no longer cause warnings in bwplot

* the default padding between components has been changed to
  0.5 "chars"


# Changes in lattice 0.14

## New features

* support for custom function that determines packet-panel
  correspondence.  This could be used to fill panels vertically
  rather than horizontally, or to split layout over two or more
  pages, etc. (see ?packet.panel.default)

* support for customizable functions for axis drawing and tick/label
  determination

* various accessor functions available to panel, strip, axis (etc)
  functions, e.g. panel.number() and packet.number()

* arguments to lattice.options and print.trellis arguments can now be
  attached to trellis objects (as parameter settings already could)
  through high level arguments 'lattice.options' and 'plot.args'

* llines, lpoints and ltext are now generic functions

* The high level 'key' argument can now have an argument called
  'reverse.rows' to reverse the order of rows.  This applies to
  'draw.key', 'auto.key' and 'simpleKey' as well.

* extended interpretation of 'breaks' in histogram()

* matrix methods for 'splom' and 'parallel' (whose absence was an
  oversight)

* support of 'alpha' argument in labels and legends, which were
  previously missing for no good reason

* panel.grid() now allows 'h' and 'v' to have negative values other
  than -1, in which case '-h' and '-v' will be used as the 'n'
  argument to pretty() when determining line locations

## Changes in behaviour

* panel function is no longer given arguments panel.number and
  packet.number (see above for alternatives)

* panel.identify() now has a more useful return value (selected
  subscripts)

* trellis.panelArgs() without any arguments should return meaningful
  results while a "trellis" object is being printed, and thus should
  be usable inside panel or axis functions.

* For formulae of the form y1 + y2 ~ x1 + x2 + x3, the order of
  levels of the artificially created grouping variable is now more
  'intuitive'


# Changes in lattice 0.13

## New features

* high level generics like 'xyplot' now have both 'x' and 'data' as
  arguments.  The only implication for S3 methods is that they will
  have to include the 'data' argument even if they are unused (as
  they should be when 'x' is not a formula).  The reason for doing
  this is to encourage S4 methods using multiple dispatch where 'x'
  is a formula and 'data' is some other data source.

* R messages are now translatable.

* French translations courtesy of Philippe Grosjean.

* instead of ignoring it as before, 'panel.xyplot' and
  'panel.densityplot' now deal with a 'groups' argument appropriately
  by calling 'panel.superpose'.  Consequently, the default of 'panel'
  in 'xyplot' etc does not need to be conditional on 'groups'.

* added 'lineheight' as a graphical parameter where appropriate.

* added a 'grid.pars' setting for arbitrary grid parameters to be
  set initially via gpar().

* For a shingle 'x', 'as.character(levels(x))' creates meaningful
  labels.

* Shingle levels can now be printed by strip.default.

* The strip function, like the panel function, is now passed
  arguments 'packet.number' and 'panel.number' (although the default
  strip function makes no use of it).

* 'panel.superpose' has new argument to make it bahave like in S-PLUS
  (interpretation of 'type').  This makes 'panel.superpose.2'
  unnecessary, although it's still available.

* Added wrappers lrect, lpolygon (and panel.rect, panel.polygon)

## Changes in behaviour

* evaluation scope: standard functions with a formula based interface
  ('lm' etc) look for variables in the formula (that are not found in
  'data') in the environment of the formula.  This was done
  inconsistently for lattice functions, which has been fixed.

* 'summary.trellis' is now more informative

* calls with explicit 'formula=' no longer work (used to give a
  warning before)

* The 'bar.fill' and 'superpose.fill' settings have been replaced
  with 'plot.polygon' and 'superpose.polygon' respectively, which are
  more consistent with other names.

* Default of 'data' changed from 'parent.frame()' to NULL.  This has
  to do with reasonable non-standard evaluation rules, and probably
  needs some more thought.

* Default Trellis settings (a.k.a. theme) changed.  See
  ?trellis.device for details

## Bug fixes

* NA-handling

* ltext now supports more 'adj' values

* scales$y$alternating now counts row numbers from top if as.table = TRUE

* miscellaneous improvements in strip.default

## TODO

* change panel.qq so that most work gets done there


# Changes in lattice 0.12

## Improvements

* panel.bwplot has a new 'stats' argument, which is a function used to
  calculate the statistics in the box and whisker plot.  Defaults
  to boxplot.stats, which was the hard-coded value earlier.

* panel.bwplot has been re-implemented.  Faster, avoids direct grid
  calls

* panel.densityplot now allows more flexible specifications of
  'plot.points', specifically, points can be jittered (the new
  default) or indicated by a `rug'.

* (more) changes in NA-handling.

* panel.superpose handles type='g' itself so that the grid doesn't
  get repeated for every group.

## New features

* All high level functions are now generic.  This change should be
  mostly transparent, but there may be some unforeseen side-effects.
  S3 generics and methods are used (this may change at some point,
  but not in the near future).  In particular, usage where the first
  argument is not actually a formula has now been formalized and is
  handled via method dispatch rather than the clumsy hacks in place
  earlier.

* The first argument of high level lattice functions has been renamed
  from 'formula' to 'x'.  This is related to the fact that these
  functions are now generic, and is intended to avoid long-term
  confusion.  The first argument is usually not named, so this should
  not cause many problems.  If the name 'formula' is explicitly
  supplied, it will be used with a warning (as long as there is no
  argument named 'x') for now, but not in future versions of lattice.

* aspect='xy' is now allowed when relation='free'

* A new function make.groups (present in S-PLUS) has been added.

* there's now panel.rect and lrect (similar to the base function
  rect)

* print.trellis has a 'draw.in' argument that can be used to specify
  a grid viewport to draw the plot in.

* strips can now be drawn on the left (as well as top) of a panel.
  This is useful for short wide panels, e.g. time series.

* 'Date' objects are recognized and axis labels formatted accordingly
  (not heavily tested)

## Changes in behaviour

* qqmath has been considerably revamped, primarily to allow grouped
  displays (the older implementation would not have allowed that even
  with a custom panel function).  In particular, the (pre)panel
  function(s) now get the raw data as opposed to already computed
  quantiles. Some old code may stop working.

* as a consequence of the above, panel.qqmath, panel.qqmathline etc
  have been rewritten and have different argument lists

* tmd has been rewritten (mostly to deal with qqmath objects), but
  this shouldn't be user-visible.

* densityplot defaults to showing points with random jitter.

* arguments panel.number and panel.counter, passed to panel functions
  that have those (or the ...) argument(s) have been renamed to
  'packet.number' and 'panel.number', which are more in line with
  standard Trellis jargon.

## Bug fixes

* identification of when 'type' should default to "density" was buggy
  (inapprpriate rounding)


# Changes in lattice 0.11

## Improvements

* panel.superpose.2 (which replicates behaviour of panel.superpose in
  S-PLUS) revamped, with new features to boot.

* panel.identify improved

* larrows improved, slightly different features.

* [xyz]lab in cloud / wireframe can now be grobs, and honors a 'rot'
  component for rotation (e.g., zlab = list(rot = 90))

## New features

* some finer controls added to parallel (actually panel.parallel)

* trellis.last.object(...) now behaves like
  update(trellis.last.object(), ...))

* "trellis" objects now have a plot method that's essentially an
  alias to the print method

* new function 'current.panel.limits' to retrieve native scales of
  current panel (only in later versions)

## Changes in behaviour

* behaviour of auto.key = TRUE now function specific

* auto.key list now allows a 'text' component

* defaults of several standard arguments now taken from
  lattice.options()

* type='g' now calls panel.grid(h = -1, v = -1) rather thanjust
  panel.grid()

* NA-handling (may have undesirable effects)

## Bug fixes

* several minor fixes


# Changes in lattice 0.10

## Improvements

* relation="free" and "sliced" now work for factors (at least, as
  well as can be expected)

* the code that constructs the layout of a lattice plot (in the print
  method for trellis objects) has been completely rewritten.  This is
  mostly transparent to the user, but as a side effect, it is now
  possible to control the details of the layout (things like the
  amount of padding around the plot, the gap between tick marks and
  labels) via the trellis settings "layout.heights" and
  "layout.widths".

* col.regions and colorkey in levelplot and wireframe now honour
  settings in effect when the object is printed, and not when the
  object was created.

* xlab, ylab, main and sub can now be grobs

* datasets get separate documentation, contributed by Kevin Wright

## New features

* lattice.options(), similar to options(), to control various aspects
  of lattice plots.  This is mostly for easier code maintainance, but
  can be useful for the user too.

* API now supports alpha-transparency (actual support is device
  dependent) where appropriate (some cases might have been missed,
  and reports of omissions would be appreciated).

* API for interacting with and enhancing Trellis plots AFTER they are
  drawn, based on grid functions seekViewport, grid.locator, etc.
  See ?trellis.focus

* aspect="iso" for `isometric' x- and y-axes.

* new 'default.scales' argument to high level functions, useful when
  writing wrappers

* convenience function 'strip.custom' to create strip functions from
  strip.default just by overriding one or more arguments

* type="H" in lplot.xy (for horizontal line).  New argument
  'horizontal' for panel.xyplot, which affects what happens for
  various 'type'-s.

* type="g" in panel.xyplot, which draws a reference grid

* the print method now (optionally) saves the (last) object printed
  in a non-visible environment.  This allows retrieval of the last
  printed object for 'update'-ing, and more importantly, to retrieve
  panel specific data for use while interacting with and enhancing
  plots after they are printed

* a summary method for trellis objects (currently pretty basic)

## Changes in behaviour

* lset has been deprecated, and trellis.par.set has been enhanced
  with equivalent usage

* the strip function now gets the whole strip area to work with, and
  is responsible for using it appropriately.  strip.default has been
  updated accordingly

* choice of color for grouped barcharts now taken from a new setting
  parameter 'superpose.fill' and not 'regions' as previously

* arguments to panel.levelplot has changed (this is related to how
  default colors are obtained, as described above).

## Bug fixes

* axes now drawn on last panel even if it doesn't fall on the border
  of the layout

* many other miscellaneous fixes, see SvnLog for some details


# Changes in lattice 0.9

## Improvements

* Axis labelling code has been rewritten to internally use S3 method
  dispatch, with (unexported) methods for numeric (default),
  character (for factors), POSIXct and date. More methods can be
  considered on request.  reversed limits are now allowed.

* contourplot can now handle missing rows in the data frame
  (equivalent to NA's in z). contourplot now uses contourLines().

* cloud and wireframe now use better 3-D projection calculations, and
  are generally much better than before.  wireframe is much faster,
  and has a better shading algorithm. It can also handle NA's and
  missing rows.

* splom (specifically panel.pairs) has more functionality, including
  the option of using different panel functions below and above the
  diagonal, user defined diagonal panels, and a table-like layout
  (similar to pairs)

* font specifications now allow for fontface and fontfamily

* much improved update method for trellis objects

* setting auto.key = TRUE now computes key at printing time,
  honouring any changes in trellis settings

## New features

* arbitrary reordering of conditioning variables, as well as of
  levels within a conditioning variable. This works in the update
  method (as well as high-level plots), making it easy to examine
  parts of a multipanel trellis display and view it in different
  conditioning orders.

* extended key functionality (via the legend argument) that allows
  multiple legends and the use of arbitrary grid objects as keys

* option to NOT drop unused factor levels when subsetting, by setting
  drop.unused.levels = FALSE or
  drop.unused.levels = list(cond = FALSE, data = FALSE)
  in high-level functions like xyplot.

* Ability to attach settings to a trellis object (rather than
  changing the global settings), via argument par.settings in high
  level calls.

* Wireframe can now draw parametrized 3-D surfaces like spheres
  (generally of the form f(u,v) = (x(u,v), y(u,v), z(u,v)), for
  (u,v) in the square [0,1] x [0,1]).

* Functionality similar to locator() (possible due to recently added
  features of grid). All panels should have predictable viewport
  names, which can be used in seekViewport() to grab a particular
  viewport. grid.locator() can subsequently be used to locate points
  in the native coordinate system of that panel.

## Changes in behaviour

* allow.multiple now defaults to TRUE (whenever it makes sense),
  since '+' in a formula is interpreted differently than S-PLUS
  anyway. As in model formulae, I(x+y) works as expected.


* default behaviour of qq and qqmath changed (from S-PLUS behaviour)
  to match corresponding base functions qqplot and qqnorm

## Bug fixes

* Fixed important bug concerning interaction of subscripts and
  subsets

* lots of other fixes, mostly obscure


# Changes in lattice 0.8

* Major change is the addition of a NAMESPACE. grid is now not
  'require()-d', but imported only. To use grid functions directly in
  lattice calls (which is a very reasonable thing to do), one needs
  to explicitly call library(grid).

* contourplot() has improved when data has NA's. Still doesn't work
  when the NA rows are completely omitted (in other words, the full
  "matrix" has to be specified, even the entries with NA).

* Clipping can now be turned off in panels and strips via the
  trellis.par.get("clip") setting.

* See Changelog for other minor changes.


# Changes in lattice 0.7

## Grouping variables

* The handling of Grouped displays has been made more consistent (and
  different from S-Plus). Whenever a groups= argument is specified,
  it is assumed that the user wants a grouped display and an attempt
  is made to honour this whenever appropriate (this ultimately
  depends on the panel function). A non-trivial addition to the list
  of functions that support this is barchart.

* Specification of legend (key) has been made slightly easier in the
  most common cases. The key is used most often in conjunction with
  the groups argument, and using the global trellis settings. The
  simpleKey function (and the auto.key argument to high level
  functions) uses the global settings to create a key with a not very
  flexible but simple interface.

* Handling of the formula argument has been extended to allow
  multiple variables on either side of the formula (with
  allow.multiple = TRUE), e.g., 
  `xyplot(y1 + y2 ~ x, data, allow.m = TRUE)`. 
  These are treated as grouped displays.

## Scales

* Some components of scales, namely tck, rot and cex, can now be
  length 2 vectors, controlling left/bottom and right/top separately.

* Some more functions (not all) now handle factors in the formula
  correctly (i.e., coerce them to numeric when factors are not
  appropriate, but use levels of the factor for labelling).


# Changes in lattice 0.6

## API change

* panel functions: In earlier versions, panel functions and prepanel
  functions were guaranteed to be passed numeric vectors as x,y (and
  z) arguments. This is no longer true. All panel functions are now
  expected to handle other possibilities. This has been done in all
  the predefined panel functions in lattice (but not in llines,
  lpoints, etc.). In practice, the only changes required are (unless
  I have overlooked something) to add calls like

```r
  x <- as.numeric(x)
  y <- as.numeric(y)
```

  at the beginning. prepanel functions can now return, as their xlim
  or ylim components, either a numeric vector of length 2 (possibly a
  DateTime object), or a character vector. The latter implies that
  the elements of this vector should be the respective axis labels,
  associated with tick marks at `1:length_of_this_vector`.


* high-level functions: The default panel functions of high level
  functions can now be different, depending on whether a groups
  argument was passed. In practice, this now happens for xyplot,
  splom and densityplot.  (densityplot has an additional high-level
  argument specifically for this, called panel.groups, which is
  passed to the panel function.)  This is a convenience feature, (and
  is inconsistent with S-Plus) in that it presumes that if the user
  has specified a groups argument, she wants it to be used, where
  appropriate.

* scales: In anticipation of future use (in nlme, for example), the
  at and labels components of scales can now be a list. Each element
  corresponds to a panel. This is thoroughly untested and not
  guaranteed to work.

* Some additional API changes associated with cloud and wireframe are
  discussed below.

## New Features and Fixes

* Mathematical Annotation; Following changes in grid 0.7, lattice now
  supports latex-style labelling using expressions. These can be used
  in almost all sensible places (an exception being in colorkey axis
  labels in levelplot/contourplot, and this is not expected to
  change).

* Date-Time Labelling: Axis labelling procedures did not recognize
  DateTime objects in earlier versions. This has been fixed. The
  routine currently used is a hack of axis.POSIXt (without the format
  option), but will hopefully improve in future.

## 3-D functions

* The 3-D functions cloud and wireframe have been greatly improved in
  terms of extensibility. The code is much cleaner, and writing new
  panel functions are much simpler. Earlier versions had a problem
  with the default placement of the labels (x/y/z-lab) and scales
  (arrows/ticks), which has been fixed. [The only major problem that
  still remains is when, in a perspective plot, the projection of the
  distant face is fully contained inside the projection of the near
  face.]

* Earlier wireframe code used an unnecessarily large amount of
  memory. This has been fixed, although speed is still not good
  (fixes are in the planing stage, and would involve changes in
  grid). drape=TRUE used to give wrong coloring, which is now fixed.

* The 'group' argument now works with wireframe, resulting in
  multiple surfaces. This is mostly satisfactory, but is not
  sophisticated enough to render intersecting surfaces properly
  (might be approximated by a fine enough grid).

* There are also some rudimentary lighting options, which can render
  the surface as being illuminated from a light source. No
  shadows. (Try shade=TRUE in wireframe.)

* Although these changes go a long way towards stabilizing
  cloud/wireframe, some further changes, especially in how the panel
  function handles the groups argument, are expected in the future.

## Known bugs

* Handling of NA values are often inconsistent and buggy. Some of
  these are not easily fixable (particularly one in contourplot), but
  some are, so bug reports on this are still welcome.

* Fonts specified in the new R font specification may not work yet.


# Changes in lattice 0.5

## Settings

* The biggest change is in the way settings are handled. Settings are
  now stored in a global list called lattice.theme, and is truly
  device-specific (i.e., settings for more than one device can be
  used concurrently).

* Improved theme management via lset and show.settings.

* Changed defaults for color postscript/pdf.

## New features

* bwplot and friends which had to have the grouping factor/shingle on
  the y-axis, can now have it on the x-axis as well. Far from
  perfect, though, since long labels can overlap with default
  settings.

* panel.superpose now accepts an additional argument called
  panel.groups (by default panel.xyplot), which is the panel function
  actually called for each subset of the data determined by
  groups. Avoids having to write something as big as panel.superpose
  for natural generalizations like interaction plots. (Related new
  panel function: panel.linejoin)

* colorkey in levelplot on all sides. Rendering of large key's much
  much faster (using grid.place suggested by Paul)

* Other minor changes (doc, more arguments etc)

* Following changes in grid, calls to base R graphics and lattice
  functions can now be mixed.


# Changes in lattice 0.4

## Overview

* Some implementation details have changed substantially. This might
  cause some old code to fail, though no such instances are known. No
  significant new features have been added, but there are several
  bugfixes (notably in levelplot). The important changes are noted
  below.

## Improvements:

* documentation restructured. There is no topic called `trellis.args'
  any more. The detailed description of the arguments common to all
  high level trellis functions can be found under help(xyplot)

* once trellis.device() is called, Lattice graphics and base R
  graphics should mix more or less seamlessly. There is an optional
  argument in trellis.device() that can deal with the first blank
  page problem, with certain restrictions.

* a (as yet very small) demo, called by demo("lattice")

* Clipping: whatever is drawn by the panel function is now clipped to
  inside the panel region. Strip texts are clipped to inside the
  strips.

* Axis tick labels by default do not overlap, some tick marks are
  left unlabelled if necessary.

* The argument list for strip.default changed to be like S

* levels() and nlevels() give sensible answers for shingles. new
  print methods for shingles and levels of shingles

* colorkey (currently used only in levelplot) can now be placed to
  the left, top or bottom as well

* new "lines" component in the par.strip.text argument that can be
  used to change the height of strips

* xlab, main etc can be double height strings (containing "\n"-s),
  the spaces allocated for these would be automatically adjusted

* strip.default now has style=5

* new panel.superpose.2 (suggested by Neil Klepeis)

* the default colour settings sometimes seem too light on a white
  background. To deal with this, there is a new setting with some
  darker colours that can be set by calling lset(theme =
  "white.bg"). see ?lset for details. This is currently in a
  proof-of-concept stage (the colors in "white.bg" were chosen just
  because I liked their names), and suggestions for better color
  schemes would be most welcome.

* show.settings() added


# Changes in lattice 0.3

## Overview

* The overall internal structure of the lattice package has changed
  considerably in verion 0.3, in particular making it far more
  readable and debuggable. However, this also means that some code
  which had worked with the earlier version might now fail. (This is
  just a discalimer, there are no known instances.)

## New Features

* (Almost) full support for the `key' argument for drawing legends

* Support for log scales

* levelplot (but no contourplot. In particular, the contour = T option
  in levelplot does not work)

* tmd now works on the output from qq

* panel function names can now be quoted strings

* scales and its x and y components can now be just a character
  string like "free" or "sliced", i.e., the relation tag can be
  omitted.

* extension to the `type' argument in panel.xyplot and
  panel.superpose to allow stair-like and histogram-like plots
  (type="s" and "h" in plot), as well as loess smooths (using the
  loess.smooth function in the modreg package).  Also, more than one
  of these options can now be used concurrently.  This allows, for
  example, a grouped plot where a grouping variable can be used to
  fit separate loess curves along with the scatter for each
  group. See example(xyplot)

* wrappers around grid functions with API-s of traditional graphics
  functions to help port existing S-Plus Trellis code. See below for
  details.

* changes in print.trellis to allow mixing of Lattice and usual R
  graphics. See below for details.

## Porting S-Plus Trellis code to Lattice

* One of the basic problems in porting existing Trellis code to R is
  the unusability of the base R functions like lines and points
  inside panel functions. To help make the changes more
  transparently, lattice now includes several wrappers around grid
  functions that provide an API similar to the corresponding base R
  functions. The list currently includes lpoints, llines, ltext and
  lsegments [update: larrows].

## Using Lattice and base R graphics concurrently

* [OBSOLETE] Grid graphics normally do not mix with usual R
  graphics. However, end-users typically might want to use lattice
  functions concurrently with traditional R graphics. To allow this
  without intermittent calls to grid.stop() and grid.start(),
  print.trellis (which ultimately does all the plotting in lattice)
  now tries to preserve the state of the device on which it plots. By
  default, library(lattice) opens a device in grid enabled mode. It
  can be reverted to non grid mode by grid.stop(). Subsequently, both
  Lattice functions and traditional graphics functions can be
  used. Devices opened by trellis.device() start in non-grid mode,
  unless grid.start() is called.

## Still Missing

* [OBSOLETE, except for the parts about piechart and scale]

* contourplot, wireframe, cloud (partially implemented) and of course,
  piechart

* Some components of scale (I haven't found a full list, so
  can't say exactly which are missing)

* Fonts

* axis labels badly implemented, no checking for overlaps.


