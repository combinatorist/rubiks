# Structure
## colors / sides
- b: blue
- g: green
- o: orange
- r: red
- y: yellow
- w: white

## opposites
- b <-> g
- r <-> o
- y <-> w

## corner joined sides
- w, r, b (as x, y, and z, respectively with the right hand rule)

## operations
- simplest operation: spinning a side clockwise*
- derived operations:
  - spinning counter is just 3 spins clockwise
  - spin the middle by spinning opposite sides

> \*This could equivalently be stated counterclockwise

Also, notice spinning one side

# Notations
## by Color
### Concept
`b1` means "spin blue 1 time"
The only other relevant counts are 2 and 3 (using mod 4).

### Convention
Spin in the clockwise direction, facing the side.

## by Axis & Direction
### Concept
Imagine putting the cube in 3 axis.
Then, `-x+` would mean "spin the negative x side in the positive direction."
You could define the direction by right-hand rule around the axis.

Now, for any operation, take the product of its side and direction.
Then on their shared edges*, operations will spin:
- against each other when product's match
- with each other when they don't match

> \*Operations on opposite sides are compared by edges that share a side.

### Convention
Use w, r, b as the positive x, y, and z directions, respectively.

> So, the default direction is the same on opposites in axis notation.
> :warning: But, in the color notation, opposites spin in opposite directions.
> :warning: The color notation also fails to indicate relationships.

## by Axis Summary
This notation combines the best of the other two.
Since, operations in the same axis commute, we can compress.
Furthermore, since we can go in either direction by modulo 4, we always go positive.
Hence, `x23` is equal to `2(-x+) + (+x-)` and we can still express the primitive `+x+` as `x01`.

# Composing Operations
Operations on any one side are trivial under modulo 4.
If you spin the same way 4 times, you return to the start.
So, to reverse a spin, you do 3 more (or go the other direction).
A 2-spin reverses itself.

> Notice operations on the same axis (even different sides) commute.
> :warning: Perhaps, the notation should group operations on an axis. :warning:


So, for composed operations, we should assume one spin has already occurred.
By convention, we treat this as x on the positive side (and direction?).
By convention, we will also take the next axis operated on as y.

The distinct non-trivial possibilities are:
```
x01
x02
x03 (vs. x01 by setting positive direction...)
x10 (vs. x03)
x11
x12
x13    (vs. self!)
x20 (vs. x02)
x21 (vs. x12 by setting positive direction)
x22    (vs. self!)
x23 (vs. x12)
x30 (vs. x01)
x31    (vs. self! or x13 by setting positive direction)
x32 (vs. x21)
x33 (vs. x11)
```

Considering `+` for `1` and `-` for `3`:
`~` means equivalent by resetting the positive side
`&` means equivalent by resetting the positive direction

There are 6 possibilities:
```
2 * 3 = (pick 1 (either direction) or double of the first side) * {0, +, 2}
```
> :warning: is that (above) correct?

```
x0+
x02
x0- & x0+
x+0 ~ x0-
x++
x+2
x+-
x20 ~ x02
x2+ ~ x-2 & x+2 (or & x2- ~ x+2)
x22
x2- ~ x+2
x-0 ~ x0+
x-+ ~ x+-
x-2 ~ x2+
x-- ~ x++ (or & x++)
```

Then,
```
y01
y02
y03
```

Then, anything in x again or z:
```
z01
z02
z03
```

And this continues, allows requiring

---




Ultimately, I'm looking for non-trivial reversals.
I may also need a way denote how final positions, regardless of the path to them.
