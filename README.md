greed
=====

## LESS-generated fluid grid system

**Greed** is meant to be used as a LESS mixin :

```less
.init-greed(12, 10px); // amount of columns (default : 12), gutter size (default : 0)
```

This will add rules to your stylesheet. Read on to see how to use them !

## Usage

```html
<div class="greed">
    <div class="row-4"> <!-- row of 4 columns -->
        <div class="col-1"> <!-- single column -->
        <div class="col-3"> <!-- triple column -->
    </div>
</div>
```

In this example, we declare a single 4 column-wide row, which we fill with one "normally-sized" column, and another which has thrice the width of its predecessor. If the `.greed` container is your main grid, it means the first column will be 25% wide and the second... yeah, right, 75%.

This also means you can easily alternate different types of columns :

```html
<div class="greed">
    <div class="row-7">
        <div class="col-3">
        <div class="col-4">
    </div>
    <div class="row-11">
        <div class="col-5">
        <div class="col-6">
    </div>
</div>
```

The maximum amount of columns (and the maximum digit on the `.row-*` blocks) logically being the one you specified when initializing the mixin.

The columns stand beside each other by being applied the `display: inline-block` rule, which means their alignment can easily be modified. Use the `.row-left`, `.row-center` and `.row-right` classes on the `.row-*` blocks to do so.

It implies the use of a kinda ugly `font-size: 0;` hack to collapse the gap between the columns. The `font-size` property is restored to `1rem` on the row's children. If you want to avoid this because you collapsed the spaces in your HTML, you can add the `.no-hack` class to the `.greed` container.

## Responsive

With a grid system being that adaptable, it was pretty hard to define fixed breakpoints, so I did not. It's up to you to decide what to do about it, with rules such as :

```LESS
@media query screen and (min-width: 9001px) { // OVER NINE THOUSAND
    .row-X {
        .col-Y {
            .to-row;
        }
    }
}
```

This rule sets `display: block;` and `width: 100%;` to the target `.col-*` blocks, and gives the second and above of them some top margin to recreate the gutters between the original rows.

## Enjoy !

Feel free to contribute to this.
