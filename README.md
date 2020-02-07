# CSS Course Notes

Different notes from the course

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

- Inline stylres (should not be used)
- #ID selectors
- class, psudo class and [attribute] selectors
- tag and psudo elements selectors 