# DashAnimator
svg supports dashed lines, and by updating the dasharray every frame you can create a variety of effects. this library provides a simple interface for managing multiple dashes on one line, moving at independent rates.

# Specs
The DashAnimator constructor takes an SVG shape element, an options object, and an optional array of Dash objects. The DashAnimator object has methods to add more Dash objects, or to remove some.

A Dash object has the following properties:

- starting point
- length
- direction
- move speed (offset delta per milisecond)
- size speed (length delta per milisecond)
- current offset

Distances/lengths can be gotten and set as either percentages of the line length or as SVG units.

The Dash object also includes an option for how to handle changes in the length of the target path (scale proportionally, align start, align end, align center.

The Dash object can also have callbacks associated with various points along its progression. These are specified as an array of objects, each with a "callback" property containing the callback function, and a "trigger" property indicating which progress event should trigger the callback.
The "trigger" property is a string consisting of a single character indicating which end of the dash is in question—either "n" for the leading or eNtering end, or "x" for the trailing or eXiting end—followed by either
1) a single character indicating one end of the line—either "s" for the Start of the line or "e" for the End.
	- or
2) a JS-parsable number, optionally followed by a precent sign. If followed by a percent sign, the number will be interpreted as a percentage of the length of the line. Otherwise the number will be interpreted as SVG drawing units (almost like pixels). Negative values and values over 100% are accepted.

Dash objects do not have style properties associated with them as those must be applied at the element level.
