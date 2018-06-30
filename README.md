
# Significative extracts from Michael Hartl tutorial "Learn Enough CSS and Layouts to be Dangerous"

I decided to do the Learn Enough CSS and Layout to Be Dangerous Tutorial to improve myself on front-end development aspects. Here is my cheatsheet to remember the key principles I learned.

## General principle 

CSS is a way of defining how elements on an HTML page look and are positioned, with styling that flows (“cascades”) down from element to element based on factors like which declaration came first, whether an element is the child of a parent element that has styles applied to it, or the specificity of the declaration.

The idea is that every element on the page is contained inside of another element, which in turn can contain other elements—like Russian nesting dolls.

In CSS, styling rules flow down from parents to children unless another style interrupts and takes priority.


## Formatting advice

### Writting CSS
CSS should be written in a separated file for a more mantainable website.
Divide up the styling into two different categories : global styles that will apply in many different places in order to create greater consistency, and individual sections that are self-contained modules of functionality or content.
Keep properties alphabetized, it will help find things much faster.
Be consistent : if using dashes as separators, use them everywhere, don’t mix them with underscores or camelcase.


### Naming classes and ids
Think in terms of how something functions or what its intent is, and it’s usually best to be specific. Make reference to a specific kind of element on the page. The names should be based on what the intended purpose is of the element on the page and should be very descriptive.
Avoid naming classes or ids after how the element looks on the page.

### Ids vs classes

Use ids only when you absolutely have to (for example, if you are using JavaScript, and then use them only for JavaScript).
Ids are considered by the browser to have a higher specificity : any styles declared in the more specific statement will take precedence over less specific styles.

Designing and developing the front-end of a site is like snapping together Legos. Use a system that’s modular. This way, you can add a class to an element and be confident that the styles from that class will be applied correctly.

#### Priority and specificity

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

#### Classes best practices

Make design choices that are modular so that your styles only affect things inside of modules instead of leaking out to affect elements site-wide. Classes should be combined like Legos to get the result we are looking for.
Multiple classes on an element are a valid usage of the class selector to have a module do slightly different things depending on placement or status.




