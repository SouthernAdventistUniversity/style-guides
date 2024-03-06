# HTML and CSS Style Guide

## Table of Contents
1. [Formatting](#1-formatting)
2. [HTML](#2-html)
3. [CSS](#3-css)

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
Prefer custom elements over `div` elements when it would make describing an area easier.

**Important:** Custom elements do not have a `display` styling set by default. To mimic standard `div` behavior, apply `display: block;` to the custom element.

Example:
```html
<!-- Not recommended -->
<div class="feature-list">

<!-- Recommended -->
<feature-list>
```

### 2.7 

### 2.7 Southern Components
A block component-based building system is used to build Southern's pages. This relies on a consistent HTML structure.

#### 2.7.1 Element Structure
Each component should start with a `<southern-component>` element.
