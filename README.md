Creating Component Variations using CSS Variables  

Consider the case where you need to build two different buttons. Same base styles, just a bit of difference.  
In this case, the properties that differ are the background-color and border-color of the variant.  
Here’s the typical solution.

Create a base class, say .btn and add the variant classes. Here’s an example markup:

<button class="btn">Hello</button>
<button class="btn red">Hello</button>
.btn would contain the base styles on the button. For example:

  .btn {
    padding: 2rem 4rem;
    border: 2px solid black;
    background: transparent;
    font-size: 0.6em;
    border-radius: 2px;
  }

  .btn:hover {
    cursor: pointer;
    background: black;
    color: white;
  }
So, where does the variant come in?

Here:

  .btn.red {
    border-color: red
  }
  .btn.red:hover {
    background: red
  }
You see how we are duplicating code here and there? This is good, but we could make it better with CSS variables.

What’s the first step?

Substitute the varying colors with CSS variables, and don’t forget to add default values for the variables!

  .btn {
     padding: 2rem 4rem;
     border: 2px solid var(--color, black);
     background: transparent;
     font-size: 0.6em;
     border-radius: 2px;
   }

   .btn:hover {
    cursor: pointer;
     background: var(--color, black);
     color: white;
   }

When you do this: background: var(--color, black) you’re saying, set the background to the value of the variable --color . However, if the variable doesn't exist, use the default value of black

This is how you set default variable values. Just like you do in JavaScript or any other programming language.

Here’s the good part.

With the variants, you just supply the new value of the CSS variable as under:

  .btn.red {
     --color: red
   }
That’s all. Now when the .red class is used, the browser notes the different --color variable value, and immediately updates the appearance of the button.  

Reference: https://medium.freecodecamp.org/everything-you-need-to-know-about-css-variables-c74d922ea855
