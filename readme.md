# Shaped

The goal of the shaped library is to provide basic charting functionality that can be plugged into a web-page or markdown document easily, and most specifically targeting the common FAQ / readme scenarios

## Stack

The following stack is used to implement shaped.

## Syntax

Shaped should be called once the page has loaded

```
const Shaped = require('shaped');

Shaped.render();
```

This will cause Shaped to attempt to render the diagram contained in any `<div>` with a class of `shaped` applied.

### Basic Flowcharts

Shapes are rendered either from left to right (default), or top to bottom (if the `#verticle` directive is present at the beginning of the diagram).

```
<div class="shaped">
</div>
```
```
<div class="shaped">
#verticle
</div>
```

#### Standalone shapes

Standalone shapes do not generate any connectors.

```
<div class="shaped">
[Square box node]
{Rounded box node}
<Diamond node>
(Circle node)
</div>
```

Standalone shapes can be nested, note that the direction of flow in a diagram is a per-diagram setting that cannot be toggled mid-diagram.

```
<div class="shaped">
[Square box node
  [Nested box node
    [Double nested box node]
    <With a double nested diamond node to boot>
  ]
  [And another nested box node]
  (And a circle node nested just for the fun of it)
]
</div>
```

#### Connected shapes

Connected shapes include either lines, or arrowed lines, connecting the shape of the diagram in the order they are created. These shapes will either flow horizontally or vertically based on the presence of the `#verticle` directive.

```
<div class="shaped">
[Square box node]-->[Connected to another square box node]
[Square box node]<--[Connected the other direction to another box node]
[Square box node]---[Connected without directionality to another box node]
[Square box node]~~>[Connected with a curved connection to another square box node]
[Square box node]<~~[Connected with a curved connection the other direction to another square box node]
[Square box node]~~~[Connected with a curved connection without directionality to another square box node]
</div>
```