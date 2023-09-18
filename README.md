# css-note

## transition

### colors

```css
.button {
  transition: color 150ms cubic-bezier(0.4, 0, 0.2, 1),
    background-color 150ms cubic-bezier(0.4, 0, 0.2, 1),
    border-color 150ms cubic-bezier(0.4, 0, 0.2, 1);
}
```

```scss
@mixin transition-colors {
  transition: color 150ms cubic-bezier(0.4, 0, 0.2, 1),
    background-color 150ms cubic-bezier(0.4, 0, 0.2, 1),
    border-color 150ms cubic-bezier(0.4, 0, 0.2, 1);
}

.button {
  @include transition-colors;
}
```

```jsx
// with tailwind
<button className="transition-colors" />
```

## animation

### squeeze

```css
.button {
  transition: transform 0.2s;
}

.button:active {
  transform: scale(0.9);
}

.button:not(:active) {
  transition: transform 0.2s;
  transform: scale(1);
}
```

```scss
@mixin squeeze {
  transition: transform 0.2s;
  &:active {
    transform: scale(0.9);
  }
  &:not(:active) {
    transition: transform 0.2s;
    transform: scale(1);
  }
}

.button {
  @include squeeze;
}
```

### ripple

```css
.button {
  position: relative;
  overflow: hidden;
  transform: translate3d(0, 0, 0);
}

.button:after {
  content: "";
  display: block;
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  pointer-events: none;
  background-image: radial-gradient(circle, #000 10%, transparent 10.01%);
  background-repeat: no-repeat;
  background-position: 50%;
  transform: scale(10, 10);
  opacity: 0;
  transition: transform 0.5s, opacity 1s;
}

.button:active:after {
  transform: scale(0, 0);
  opacity: 0.2;
  transition: 0s;
}
```

```scss
@mixin ripple {
  position: relative;
  overflow: hidden;
  transform: translate3d(0, 0, 0);
  &:after {
    content: "";
    display: block;
    position: absolute;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    pointer-events: none;
    background-image: radial-gradient(circle, #000 10%, transparent 10.01%);
    background-repeat: no-repeat;
    background-position: 50%;
    transform: scale(10, 10);
    opacity: 0;
    transition: transform 0.5s, opacity 1s;
  }
  &:active:after {
    transform: scale(0, 0);
    opacity: 0.2;
    transition: 0s;
  }
}

.button {
  @include ripple;
}
```

## styles

## decoration

```css
element {
  position: relative;
}

element::before {
  content: "";

  background: linear-gradient(90deg, orange 0%, rgba(255, 165, 0, 0.00) 100%);
  opacity: 0.3;

  border-top-left-radius: 40px;
  border-bottom-left-radius: 20px;

  width: 120%;
  height: 50%;

  position: absolute;
  bottom: 0;
  left: 0;
}
```
