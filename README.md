# Advanced jQuery

## Event Delegation

Let's look at a click event that we have seen before.

```html
<ul>
    <li>Riyadh</li>
    <li>Boston</li>
    <li>Jeddah</li>
</ul>
```

```js
$("li").on("click", function(event){
    $(event.target).css("color", "red")
})

```

When we `click` on an `li` then the css font color fo that `li` changes to red.

However when we add a new `li` dynamically, the click event does not work on that `li`.

```html
<ul>
    <li>Riyadh</li>
    <li>Boston</li>
    <li>Jeddah</li>
</ul>
```

```js
$("li").on("click", function(event){
    $(event.target).css("color", "red")
})

// could also be added by a user submitting a form
$("ul").append("<li>New York</li>");
```

The click event works on the `li` for `Riyadh`, `Boston`, and `Jeddah` but not on `New York`.  This is because the click event was added BEFORE the `New York` `<li>` was appended to the DOM.

We can fix this by using **event delegation**.

```js
$("ul").on("click", "li", function(event){
    $(event.target).css("color", "red")
})

// could also be added by a user submitting a form
$("ul").append("<li>New York</li>");
```

Notice how we select a parent element that IS on the page when the page originally loads and we tell it to listen for a click even on its children that are an `li`.

### Lab

- Open the [event-delegation/index.html](event-delegation/index.html]) file in the browser. 
- Add a new `li` by submitting the form
- Notice how the click event works on the other `li`s but not the new one
- Use event delegation in [event-delegation/main.html](event-delegation/main.js]) to fix the problem so that the click event works on even dynamically added `li`s.

## Group Project

With your group, you are going to build a fully functioning To Do List application using jQuery.  The HTML and CSS has already been completed for you.  It is up to you and your team to write the jQuery and Javascript to make the To Do List function.  Every team member should be coding along together and have their own copy of the code.  Work together and make sure every team member understands the code.

- The [pseudo code is here](to-do-list/pseudocode_suggestions.md)
- Your [starter code is here](to-do-list)