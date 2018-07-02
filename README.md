
# Significative extracts from Michael Hartl tutorial "Learn Enough CSS and Layouts to be Dangerous"

*I decided to do the Learn Enough CSS and Layout to Be Dangerous Tutorial to improve myself on front-end development aspects. Here is my cheatsheet to remember the key principles I learned.*


## General principle 

CSS is a way of defining how elements on an HTML page look and are positioned, with styling that flows (“cascades”) down from element to element based on factors like which declaration came first, whether an element is the child of a parent element that has styles applied to it, or the specificity of the declaration.

The idea is that every element on the page is contained inside of another element, which in turn can contain other elements—like Russian nesting dolls.

In CSS, styling rules flow down from parents to children unless another style interrupts and takes priority.


## Formatting advice

### Writting CSS

* CSS should be written in a separated file for a more mantainable website.
* Divide up the styling into two different categories : global styles that will apply in many different places in order to create greater consistency, and individual sections that are self-contained modules of functionality or content.
* Group all styles that relate to the same part of the site in the same place, and to be extra helpful add in a comment or two that explains what the styles are for
* Be consistent in the naming convention : if using dashes as separators, use them everywhere, don’t mix them with underscores or camelcase.
* Keep the number of selectors in a declaration under three for a good readability and limit the work the browser has to do to render the page.
* Keep properties alphabetized, it will help find things much faster.


## Ids and classes

### Naming classes and ids

Think in terms of how something functions or what its intent is. The names should be based on what the intended purpose of the element is on the page, and should be very descriptive.
It’s usually best to be specific : make reference to a specific kind of element on the page. 
Avoid naming classes or ids after how the element looks on the page.

### Ids vs classes : how to use them ?

Use ids only when you absolutely have to (for example, if you are using JavaScript, and then use them only for JavaScript).
Ids are considered by the browser to have a higher specificity : any styles declared in the more specific statement will take precedence over less specific styles.

Designing and developing the front-end of a site is like snapping together Legos. The system used should be modular. Design choices that are modular assure you that your styles only affect things inside of modules instead of leaking out to affect elements site-wide. Classes should be combined like Legos to get the result we are looking for. This way, you can add a class to an element and be confident that the styles from that class will be applied correctly. Multiple classes on an element are a valid usage of the class selector to have a module do slightly different things depending on placement or status.

### Priority and specificity

|Priority rank  |Name                |Situation                                                                                       |
|:-------------:|:------------------:|:----------------------------------------------------------------------------------------------:|
|1              |Importance          |Adding !important (e.g., “width: 100% !important”) to a value overrides all other similar styles|
|2              |Inline              |A declaration that is put on an element using style=                                            |
|3              |Media Type          |When a style is applied through a media query                                                   |
|4              |User defined        |Most browsers have the accessibility feature: a user defined CSS                                |
|5              |Selector specificity|Styling applied via a class or id overwrites generic styling                                    |
|6              |Rule order          |The last style written has priority                                                             |
|7              |Parent inheritance  |If there is no style specified, then children inherit styles from their parent                  |
|8              |CSS                 |CSS rules from a stylesheet or style block that are applied to generic elements.                |
|9              |Browser defaults    |Lowest priority, these are the default styles that browsers ship with                           |

|Situation                                             |Example                           |Specificity rank|
|:----------------------------------------------------:|:--------------------------------:|:--------------:|
|Simple HTML selector                                  |em {color: #fff;}                 |1               |
|HTML selector targeting element inside another element|h1 em {color: #00ff00;}           |2               |
|CSS class name                                        |.alert {color: #ff0000;}          |1,0             |
|HTML element with a class name                        |p.safe {color: #0000ff;}          |1,1             |
|CSS id                                                |#thing {color: #823706;}          |1,0,0           |
|CSS id with a class name                              |#thing .property {color: #823706;}|1,1,0           |
|Inline style                                          |style="color: transparent;"       |1,0,0,0         |

## Sizing

### Best practices

The browser sets a default margin on the html and body tags. The solution is to reset the default styles using CSS.
Using relative sizes helps deal with the different screen scale issues, and also allows for easy resizing of the contents of a page.


### Percentages

* Percentage sizing is based on the parent container that an element is wrapped by. It isn’t determined by the size of the browser, or the page as a whole.
* Percentages don't work for borders
* Percentage heights are a little weird because they require a set height on the parent element—they can’t just assume a height the way that they assume a width.
* If you use a percentage for a text size, the resulting size of the font is based not on the pixel dimensions of the container but rather on whatever font-size style that container has inherited.

### em

One em represents a number of pixels equal to the current font size of any given element’s parent container. If there is no font size that is inherited, then the default page font size is used (16px).
Ems are useful : they automatically change value based on the font size that is inherited by the parent object that they are contained in. By changing a single base font size, all the fonts in all the child containers will resize in correct proportion based on this new declared font size.
Em units are cumulative: if an element that has its font size set to 0.5em appears inside an element whose font size is also 0.5em, then the resulting font size for that bottom child element is 0.5×0.5 = 0.25em.
Em unit can be used for things like margin, padding, and width. In those cases, the size of an em is based on the local font size, so if you set a width for an object in em it will size the object based on the font size inside that element.
Doing your sizing using ems, all your elements and their attributes like padding or margin will be sized relative to the size of text. But just because we want to increase the size of fonts on a page doesn’t necessarily mean that we also want to change something like margin or padding. Don't use em for margin or padding if you want the boxes that hold the content to stay the same and only the stuff inside to change.

### rem (root em)

Rem unit works similarly to em. It is a percentage of an absolute font size, but instead of being cumulatively sized based on the whole parent/child tree, the rem unit always refers back to the font size of the html tag, the most basic font size for the whole page (the default size is 16px). 
You can set the size of elements like boxes, or font sizes, and have them all tie back to a single value: the font size of the html tag. If you want to make everything a little bigger, or smaller, you can change just this one font size and everything on the page adapts.
rem is especially useful in combination with em units in developing modules. The best practice is to set a font size for the module’s wrapper using a rem unit, and then style the fonts inside using em units.

### vh (viewport height), vw (viewport width)

These units allow us to size elements on the page based on the actual size of the browser window or mobile device screen.
Each vh or vw is 1 percent of the corresponding screen dimension, so 3vh would equal 3% of the height of the screen and 100vw would be 100% of the width. Viewport dimensions work for fonts too.
Everything is determined by the size of the browser window or device screen.
Using vh and vw for everything, the site would look bad on either mobile or desktop (depending on which platform you were using when you designed the page).

### Font sizes

The goal should always be to have readable text on the page. Nicely laid-out copy should be the equivalent of somewhere between 14px and 18px in height.
Use relative units for text, and simply pick random numbers that set the font sizes somewhat close to what your design calls for.

## Box model

### Inline vs block

All of the elements that modify text, such as "strong" and "em", are inline elements. Other common inline elements include links and (perhaps surprisingly) images.
Inline elements take up only as much width on the page as is necessary to contain the content inside the tags—you can think of inline elements as being shrink-wrapped around the content inside them.

Block elements always start on a new line, as if there is a line break in front of them, so one of their main purposes is to divide the page’s text into different presentational groups, such as paragraphs or lists. Block elements bound the full width of the page, like an inflexible cardboard box.

Inline elements are only allowed to have margins and padding applied to the left and right (not top or bottom), and they won’t accept a width or height set by CSS. None of these restrictions apply to block elements.
Some styles can cause an inline element to switch to be a block element. Changing an element’s position on the page can also switch it from inline to block

It is possible to directly force an element to change :
* display: none prevents the element from displaying on the page.
* display: block forces an element to be a block element regardless of what it was before.
* display: inline turns a block element into an inline element. The element will no longer be on its own line, but rather will flow with text like any other inline element. 
* display: inline-block is a hybrid between inline and block. It allows styling that normally works only on block elements—such as width and height, top margins, and padding—to be applied to a particular element. At the same time, it also lets the element as a whole act like an inline element. Inline-block declaration is especially helpful when making site navigation, or when styling a group of elements so that they are side by side.
* display: flex is a powerful display property that forces all child elements to fill the entire parent element, and is highly customizable to allow for incredibly useful layout possibilities.

### Margins, padding, and borders

In the default state, CSS assumes that when you set a size for an element you are only talking about the content part of an element. Elements and their content are not the same thing.

box-sizing: border-box property cause the browser to draw the borders and padding inside of the defined width.

When elements aren’t block elements, the browser fully respected their set margins. When two block elements with margins follow each other, one of the top or bottom margins is canceled out.

### Floats

When you set an element to float to the left or right, all the inline content around it will flow around the floated element. Floated elements will always sit next to other floated elements on the same line, as long as there is horizontal room. If the elements are too wide, they will drop down to the next line.
The problem is that the browser doesn’t always know where to end the float. The clear rule is used to let the browser know to end floats. If the floating elements had been floated to the right using float: right, you would need to clear their float status with clear: right, or  you can clear both types of floats using clear: both. A better way to clear floats is apply a rule to clear everything inside a wrapper with :
* overflow: hidden but the if you also need to set a height or width on the element that has overflow: hidden set, the content inside can get cut off.
* :after

