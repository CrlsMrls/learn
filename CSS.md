# CSS

# Basic Selectors

## Type selector
The CSS type selector matches elements by node name. In other words, it selects all elements of the given type within a document.

```
element { style: property }
```

## Class selector
Selects all elements that have the given class attribute.

```
.classname { style: property }
```

## ID selector
Selects an element based on the value of its id attribute. There should be only one element with a given ID in a document.

```
#id_value { style: properties }
```
## Universal selector
Selects all elements of any type (optionally, it may be restricted to a specific namespace).

```
* { style: properties }
```

## Attribute selector
Selects elements based on the value of the given attribute.

Examples:
`[attr]` - Represents an element with an attribute name of attr.
`[attr=value]` - Represents an element with an attribute name of attr whose value is exactly value.
`[attr~=value]` - Represents an element ... whose value is a whitespace-separated list of words, one of which is exactly value.


# Combinators


## Descendant combinator
The combinator selects nodes that are descendants of the first element. In other words, elements matched by the second selector are selected if they have an ancestor element matching the first selector.
**Syntax:** `A B`
**Example:** `div span` will match all <span> elements that are inside a <div> element.

## Child combinator
The > combinator selects nodes that are **direct children** of the first element.
**Syntax:** `A > B`
**Example:** `ul > li` will match all <li> elements that are nested directly inside a <ul> element.

## Adjacent sibling combinator
The + combinator selects adjacent siblings. This means that the second element directly follows the first, and both share the same parent.
**Syntax:** `A + B`
**Example:** h2 + p will match all <p> elements that directly follow an <h2>.

## General sibling combinator
The ~ combinator selects siblings. This means that the second element follows the first (though not necessarily immediately), and both share the same parent.
**Syntax:** `A ~ B`
**Example:** p ~ span will match all <span> elements that follow a <p>.


# CSS pseudo-class
A CSS pseudo-class is a keyword added to a selector that specifies a special state of the selected element(s). 
Pseudo-classes allow the selection of elements based on state information that is not contained in the document tree.

Examples of pseudo-classes:
:disabled - represents any disabled element
:first-child - the first element among a group of sibling elements
:last-child - the last element among a group of sibling elements
:nth-child() - elements based on their position in a group of siblings. 
-- :nth-child(2n) - even 
-- :nth-child(7) - seventh element (starts at 1)
:focus - that has received focus

# CSS pseudo-element
A CSS pseudo-element is a keyword added to a selector that lets you style a specific part of the selected element(s).
Pseudo-elements represent entities that are not included in HTML.

Examples:
::after - the last child of the selected element
::before - the first child of the selected element. 


