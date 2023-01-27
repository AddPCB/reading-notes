# 04 notes

## html

To create a basic link, we wrap text or other content inside the `<a>` element.

The `href` attribute contains the URL of the page or file to which the link is pointing.
To ensure links on our pages are accessible to all readers, we can:

- Provide descriptive link text, so readers know what they will find when they click the link.
- Add a `title` attribute to the link, so screen readers can read a brief description of the link's destination.
- Use the `tabindex` attribute to make sure keyboard users can access the link.
- Add `aria-label` attributes to provide additional context to readers.

## css

`Normal flow` means that HTML elements are positioned according to their source order, with each element flowing from top to bottom and left to right.

A few differences between `block-level` and `inline` elements include:

- `Block-level` elements occupy the entire `width` of the page, while `inline` elements only take up as much space as necessary.

- `Block-level` elements can have `width` and `height` specified, while `inline` elements cannot.

`Static` positioning is the default for every HTML element.
A few advantages to using `absolute` positioning on an element include:

- It allows elements to be placed at exact locations on the page.

- It can be used to `layer` elements on top of each other.

- It allows elements to be placed outside of their parent containers.

A key difference between `fixed` positioning and `absolute` positioning is that a `fixed` element stays in the same position even when the page is scrolled, while an `absolute` element will move with the page when it is scrolled.

## js

The difference between a function declaration and a function invocation is that a function declaration is the definition of the `function`, while a function invocation is when the code is actually executed.

The difference between a `parameter` and an `argument` is that a `parameter` is the `name` used to define a `function`, while an `argument` is the `value` passed to the function when it is invoked.

Here is a short unordered list with inline code examples:

- Function declaration: `function myFunction(parameter1, parameter2) { // code goes here }`

- Function invocation: `myFunction(argument1, argument2);`

- Parameter: function `myFunction(parameter1, parameter2) { // code goes here }`

- Argument: `myFunction(argument1, argument2);`
