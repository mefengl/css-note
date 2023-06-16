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
