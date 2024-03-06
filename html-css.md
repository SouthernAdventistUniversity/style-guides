# HTML and CSS Style Guide

## Table of Contents
1. [Formatting](#1-formatting)
2. [HTML](#2-html)
3. [CSS](#3-css)
4. [Southern Components](#4-southern-components)

## 1. Formatting
### 1.2 Indentation
Indent by 2 spaces at a time. Do not mix spaces and tabs.

### 1.3 Capitalization
All code should be lowercase.

## 2. HTML
### 2.2 Semantics
Use elements for what they have been created for. For example, use `heading` elements for headings, `p` elements for paragraphs, `a` elements for anchors, etc.

Using HTML according to its purpose is essential for accessibility, reuse, and code efficiency.
```html
<!-- Not recommended -->
<div onclick="goToRecommendations();">All recommendations</div>

<!-- Recommended -->
<a href="recommendations/">All recommendations</a>
```

### 2.3 Multimedia Fallback
All multimedia elements (ex. `img`, `video`, etc.) should have an alternate content provided via the `alt` attribute.

For images where an `alt` attribute would introduce redundancy or for purely decorative images, do not provide alternative content.

### 2.4 `id`, `class`, `name`, and `data` attributes
Avoid unnecessary `id` attributes.

Prefer `name` for reusable components, `class` attributes for reusable styles, and `data` attributes for scripting/modes.

`data` attributes are preferred over classes for more declarative values or modes.

Example:
```html
<!-- Not recommended: class name 'v1' is not reusable for other elements and not descriptive -->
<southern-component id="hero" class="v1">

<!-- Recommended: name is reusable, version is descriptive -->
<southern-component name="hero" data-version="interior">
```

Where `id` attributes are strictly required, always include a hyphen in the value to ensure it does not match the JavaScript identifier syntax, e.g. use `user-profile` rather than just `profile` or `userProfile`.

### 2.5 Quotation Marks
When quoting attribute values, use double quotation marks.

Example:
```html
<a href="#user-profile">Profile</a>
```

### 2.6 Custom Elements
Prefer [custom elements](https://developer.mozilla.org/en-US/docs/Web/API/Web_components/Using_custom_elements) over `div` elements when it would better describe an area.

**Important:** Custom elements do not have a `display` styling set by default. To mimic standard `div` behavior, apply `display: block;` to the custom element.

Example:
```html
<!-- Not recommended -->
<div class="feature-list">

<!-- Recommended -->
<feature-list>
```

## 3. CSS
### 3.1 Style Rules
#### 3.1.1 Class Naming
Use meaningful or generic class names. Names should reflect the purpose of the class.

#### 3.1.2 Class Name Delimiters
Words in class names should only be separated by a **hyphen**.

Example:
```css
/* Disallowed */
.this_123 {}
.twowords {}

/* Recommended */
.list-item {}
```

#### 3.1.3 Type Selectors
Unless necessary (for example with helper classes), do not use element names in conjunction with classes.

```css
/* Not recommended */
ul.example {}
div.error {}

/* Recommended */
.example {}
.error {}
```

#### 3.1.4 ID Selectors
Avoid ID selectors. IDs are expected to appear only once on a page, so name or class selectors should be preferred.

For components: prefer `name` selectors:
```css
southern-component[name=hero]
```

#### 3.1.5 Units
Prefer relative units such as `rem`, `ch`, `vh`. `px` is accepted but not encouraged.

Unless required, do not provide a unit when setting a property to a value of `0`.

[Learn about units](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Values_and_units).

#### 3.1.6 Leading 0s
Always include leading “0”s in values.

Put `0`s in front of values or lengths between -1 and 1.

```css
font-size: 0.8rem;
```

### 3.2 Formatting Rules
1. Indent block content.
2. Use a semicolon after every declaration.
3. Use a space after a property name's colon.
4. The opening brace of a declaration block should be on the same line as the last selector, with a single space in between.
5. Separate rules by new lines.
6. Use single quotes instead of double quotes.
7. If possible, group style sheet sections together by using comments.

```css
/* Not recommended: missing space before opening brace and after property name colon */
.video{
  margin-block-start:1rem;
}

/* Not recommended: unnecessary line break, double quotes, and no ending semicolon */
.video
{
  margin-block-start: 1rem;
  font-family: "open-sans"
}

/* Recommended */
.video {
  margin-block-start: 1rem;
  font-family: 'open-sans';
}
```

## 4. Southern Components
A block component-based building system is used to build Southern's pages. This relies on a consistent HTML structure.

### 4.1 Element Structure
Each component should start with a `<southern-component>` element and contain only two elements:
1. `<component-header>`
    1. This should contain only one `h2` and one `p` element in that order.
    2. Can be omitted if the component does not use a header or description.
3. `<component-content>`
   1. All other component markup should be placed here.

Example:
```html
<southern-component name="c02" data-version="standard">
  <component-header>
    <h2>Header</h2>
    <p>Description</p>
  </component-header>
  <component-content>
    ...
  </component-content>
</southern-component>
```
These three custom elements have base styles applied automatically.

### 4.2 `data` attributes
Coming...
