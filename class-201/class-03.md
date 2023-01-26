# Class 3 reading

## Learn HTML

- When you want to list several items without indicating the order of importance, you should use an unordered list in your HTML document.

- To change the bullet style of unordered list items, you can use the list-style-type property on the `<ul>` or `<li>` tags.

- When you need to indicate the order of importance, you should use an ordered list.

- To change the numbers on list items provided by an ordered list, you can use the list-style-type property on the `<ul>` or `<li>` tags, or you can use the start attribute on the `<ol>` tag.

## Learn CSS

- In "The Box Model" story, the CSS properties of margin and padding can be thought of as two characters: Margin and Padding. Margin is the space outside the border of an element, while Padding is the space inside the border. Both of them play a critical role in controlling the size and shape of elements within a web page.

- The four parts of an HTML element's box are the margin, border, padding, and content. The margin is the space outside the border of the element. The border is the line that defines the edge of the element. The padding is the space between the border and the content of the element. Finally, the content is the actual information contained within the element.

## Learn Javascript

- The people array is a valid JavaScript array:

```javascript
const people = [['pete', 32, 'librarian', null], ['Smith', 40, 'accountant', 'fishing:hiking:rock_climbing'], ['bill', null, 'artist', null]];
```

You can access the values stored in the array by using bracket notation, for example: `people[0]` will return `['pete', 32, 'librarian', null]`.

To access the individual values within the subarrays, you can use two sets of bracket notation, for example: `people[0][1]` will return `32`.

## Things i want to know more about:

### Template strings.

We have been taught to include variables in output like this:

```javascript
console.log(myName + " scored " + correctAnswers + "points out of 7.");
```

But VScode suggests we do this, which seems more intuitive:

```javascript
\`Colour picked: ${question7}. Attempts remaining: ${q7Attempts}.\`
```
