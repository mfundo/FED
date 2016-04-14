# BEM Style Guide

1. [Anatomy of a Ruleset](#anatomy-of-a-ruleset)
2. [Formatting](#formatting)
3. [Multi-line CSS](#multi-line-css)
4. [Indenting](#indenting)
5. [Meaningful Whitespace](#meaningful-whitespace)
6. [Declaration order](#declaration-order)
7. [BEM](#bem)


# Anatomy of a Ruleset

* When using multiple selectors in a rule declaration, give each selector its own line.
* The opening brace ( { ) is on the same line as the last selector.
* Use a space before the opening brace ( { ).
* The closing brace ( } ) is on a new line after the last declaration.
* [property] and [value] are on the same line.
* Include one declaration per line in a declaration block.
* Use one level of tab indentation for each declaration.
* The first declaration is on a new line after the opening brace ( { ).
* Use a space after the property–value delimiting colon ( : ), but not before.
* Use a trailing semi-colon ( ; ) on the last declaration.

### Bad

```ruby
.selector1, .selector2 
{
    [property] : [value]; [property] : [value];
}
```

### Good

```css
.selector1, 
.selector2 {
    [property]: [value]; 
    [property]: [value];
}
```

# Formatting

* Prefer dashes over camelCasing in class names.
* Use lowercase in class names.
* Do not use ID selectors.
* Use lowercase and shorthand hex values, e.g., #aaa.
* Use double / single quotes consistently. e.g., content: "".
* Quote attribute values in selectors, e.g., input[type="checkbox"].
* Avoid specifying units for zero-values, e.g. margin: 0;
* Include a space after each comma in comma-separated property or function values

### Bad

```css
#Selector1, 
.Selector2 {
    [property] : '[value]'; 
    [property] : "[value]";
    [property] : 0;
}
```

### Good

```css
.selector1, 
.selector2[type="text"] {
    [property]: "[value]"; 
    [property]: "[value]";
    [property] : 10px;
}
```

# Multi-line CSS

* CSS must be written across multiple lines

### Bad

```css
.selector1, .selector2 { [property] : [value]; [property] : [value]; }
```

### Good

```css
.selector1, 
.selector2 {
    [property]: [value]; 
    [property]: [value];
}
```

# Indenting

* Use one level of tab indentation for each declaration.
* Never mix spaces and tabs for indentation.

### Bad

```css
.selector1 { 
  [property] : [value]; 
 
    &__element1 {
      [property] : [value]; 
    }
}
```

### Good

```css
.selector1 { 
    [property] : [value]; 
 
    &__element1 {
        [property] : [value]; 
    }
}
```


# Meaningful Whitespace

* Whitespace should always be consistent.
* One (1) empty line between related rule sets.
* Two (2) empty lines between entirely new sections.

### Example

```ruby
.selector1 {
    &__element1 {
    
        &--modifier { }
    
    }

    &__element2 {}
 }
      
.selector2 {
    &__element1 {}
    
    &__element2 {}
}
```

# Declaration Order

* Use alphabetical ordering of declarations or group them by layout, design etc.

### Example

**Alphabetical**
```css
.selector1 {
    font-size: 10px;
    line-height: 1em;
    margin: 10px;
    padding: 10px
}
```

**Functional grouping**
```css
.selector1 {
    display: flex;
    margin: 10px;
    padding: 10px;
    background: crimson;
    font-size: 10px;
    line-height: 1em;
}
```

# BEM

| Block                                                                                      | Element                                                                                    | Modifier                                                                                   | 
|--------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
| The sole root of the component.                                                            | A component part of the Block.                                                             | A variant or extension of the Block.                                                       |
| **Example**                                                                                    | **Example**                                                                                    | **Example**                                                                                    |
| header, container, menu, list, button, checkbox, input                                     | menu item, list item, checkbox caption, title                                              | disabled, highlighted, checked, fixed, size, color                                         |
                                                                                       |
| **.block {}**                                                                                  | **.block__element {}**                                                                                    | **.block--modifier {}**                                                                                  |

### Example/Analogy

```css
.person {}
.person__head {}
.person--tall {}
```

- **.person {}** is the Block; it is the sole root of a discrete entity.
- **.person__head {}** is an Element; it is a smaller part of the **.person {}** Block.
- **.person--tall {}** is a Modifier; it is a specific variant of the **.person {}** Block.

## Block Context

* Block context starts at the most logical, self-contained, discrete location.
* BEM applies to self-contained, discrete parts of the UI.

If we have a **.person {}** inside a **.room {}**, it is more correct to use self contained selectors which bridges two Blocks than it is to increase the scope of the existing Blocks and Elements.
This will allow the **.person {}** and **.room {}** Blocks to be used independently or together.

### Bad
```ruby
.room {}
    .room__person {}
        .room__person__head {}
            .room__person__head--tall {}
```

### Good
```ruby
.room {}

.person {}
    .person__head {}
    .person--tall {}
```

## Block Layers

If we were to add another Element—called **.person__eye {}** to the **.person {}** component, we would NOT need to step through every layer of the DOM.

### Bad
```ruby
.person {}
    .person__head {}
        .person__head__eye {}
```

### Good
```ruby
.person {}
    .person__head {}
    .person__eye {}
```
