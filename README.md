# CSS Course Notes

Different notes from the course

## Mozilla Developer CSS reference
- Most important CSS resource online: https://developer.mozilla.org/en-US/docs/Web/CSS/Reference
- Most common CSS Properties: https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Properties_Reference
- MDN CSS Specifity: https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity

## Cascading Style Sheets & Specifity

In what order are css rules compiled and what priority do they get.

    .my-class {
        color: red;
    }

    h1 {
        color: blue;
    }

    h1 {
        color: green;
    }

CSS file is read and compiled top from bottom. The last rule match will have higher priorty then the previous one.

    <h1> would be green </h1>
    <h1 class="my-class"> would be red </h1>

How conflicts are resolved:

- Inline styles (should not be used)
- #ID selectors
- class, psudo class and [attribute] selectors
- tag and psudo elements selectors 
- Browser defaults
- Inherited styles

You will see that the higher the specifity the higher the priority
on a match. More specific rule has a higher specifity.

When you inspect Styles in DevTools of the browsers you will see that the imported style order is iverted.
The highest priority is at the top. 

## Combinators

Unterstanding combinators.

### Adjecant Sibling +
Apply color red to paragraf tag (p) when its directly following a h2 tag,

    h2 + p {
        color: red;
    }

Will apply to:

    <div>
        <h2>Not applied</h2>
        <p>CSS applied</p>
        <h2>Not applied</h2>
        <h3>Not applied</h3>
        <p>Not applied</p>
        <h2>Not applied</h2>
        <p>CSS applied</p>
    </div>

Rules:
- Elements share them same parent
- Second element comes immedialty after first element

### General Sibling ~
Same as adjencant, but doesn't have to directly follow the h2.
    h2 ~ p {
        color: red;
    }

Will apply to:

    <div>
        <h2>Not applied</h2>
        <p>CSS applied</p>
        <h2>Not applied</h2>
        <h3>Not applied</h3>
        <p>CSS applied</p>
    </div>

Rules:
- Elements share the same parent
- Second element comes after first element

### Child >
Any paragrap that is a direct child of this div should get the defined style.

    div > p {
        color: red;
    }

Will apply to:

    <div>
        <div>Not applied</div>
        <p>CSS applied</p>
        <h2>Not applied</h2>
        <h3>Not applied</h3>
        <p>CSS applied</p>
    </div>

Rules:
- Second element is a direct child of the first element

### Descendant
**NB: probably the one you should use most ofte**
Here the level of child does not matter. Must just be a descendant.

    div p {
        color: red;
    }

Will apply to:

    <div>
        <div>Not applied</div>
        <p>CSS applied</p>
        <h2>Not applied</h2>
        <h3>Not applied</h3>
        <article>
            <p>CSS applied</p>
        </article>
        <p>CSS applied</p>
    </div>

Rules:
- Second element is just a descendant of the first element.

## Box Model

### Margin Collapsing

Margins between two boxes are collapsed, and the
bigger margin wins. This can sometimes be hard to
maintain and best practice is to exclusively use
`margin-top` or `margin-bottom`.

### Separate vs Shorthand Properties

Normal properties that combine the properties into one shorthand style property.
Example:

    border-width: 2px;
    border-style: dashed | solid;
    border-color: orange;
    
    ... can be written also as ...
    
    border: 2px dashed orange;
    
Order does not matter unless properties use the same value.


    margin-top: 5px;
    margin-right: 10px;
    margin-bottom: 5px;
    margin-left: 10px;
    
    ... can be written as ...
    
    margin: 5px 10px 5px 10px // top right bottom left 
    margin: 5px 10px // (top & bottom) (left & right)
    margin: 10px // 10px on all sides
            
Again a design decision if they should be used. Be more or less explicit in 
you css file. 
    
You can use the browser dev tools css layout property drop down on shorthands to see
all values set in the shorthand, and the correct order of them. 
    
    
    
    
