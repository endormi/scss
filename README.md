# SCSS

`SCSS` variables, mixins and media queries.

Variables:

```scss
$font-stack: "Helvetica Neue", Helvetica, Arial, sans-serif;

* {
    font-family: $font-stack;
}
```

Mixins: 

```scss
@mixin push-auto {
    margin: {
      left: auto;
      right: auto;
    }
  }

* {
    @include push-auto();
}
```

CSS Breakpoints:

```scss
$breakpoints: (
    "mobile": 400px,
);

@mixin media_queries($width, $type: max) {
    @if map_has_key($breakpoints, $width) {
        $width: map_get($breakpoints, $width);
        @if $type == max {
            $width: $width - 1px;
        }
        @media only screen and (#{$type}-width: $width) {
            @content;
        }
    }
}

@include media_queries('mobile') { 
    li { 
        color: rgb(4, 0, 255);
    }
}
```