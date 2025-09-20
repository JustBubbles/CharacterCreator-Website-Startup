# Git Commands:
```
  git fetch #gets the most recent info on the most recent changes to the repository. Doesn't affect your version.
  git status #tells you the difference between your version and the version you have info on.
  git pull #updates your code to the same as the github repository.
```
# Git Bash Commands
```
  echo - Output the parameters of the command
  cd - Change directory
  mkdir - Make directory
  rmdir - Remove directory
  rm - Remove file(s)
  mv - Move file(s)
  cp - Copy files
  ls - List files
  curl - Command line client URL browser
  grep - Regular expression search
  find - Find files
  top - View running processes with CPU and memory usage
  df - View disk statistics
  cat - Output the contents of a file
  less - Interactively output the contents of a file
  wc - Count the words in a file
  ps - View the currently running processes
  kill - Kill a currently running process
  sudo - Execute a command as a super user (admin)
  ssh - Create a secure shell on a remote computer
  scp - Securely copy files to a remote computer
  history - Show the history of commands
  ping - Check if a website is up
  tracert - Trace the connections to a website
  dig - Show the DNS information for a domain
  man - Look up a command in the manual
```
# Chaining Git Bash Commands
```
  | - Take the output from the command on the left and pipe, or pass, it to the command on the right
  > - Redirect output to a file. Overwrites the file if it exists
  >> - Redirect output to a file. Appends if the file exists
```
## Example:
This finds all files that were created in November, using grep to find them \("Global Regular Expression Print\), and count how many of them there are.
`ls -l | grep ' Nov ' | wc -l`

# Git Bash Console Shortcuts
```
CTRL-R - Use type ahead to find previous commands
CTRL-C - Kill the currently running command
```
# How to SSH into a server. 
```
ssh -i [key pair file] ubuntu@[ip address]
```
Server Public IP: 98.87.60.92

## How to Keep the Same Public IP Address
"You have two choices in order to keep the same public IP address:

Never stop your server.
Assign an elastic IP address to your server so that it keeps the same address even if you stop it.
Your first elastic IP address is free. However, the catch is that it is only free while the server instance it is assigned to is running. While your server is not running you are charged $0.005/hr. This is the same cost for running a t3.nano server instance. So if you assign an elastic IP address, you don't save any money unless you are running a more powerful instance, and are stopping your instance when you, or the TAs, don't need it.

We would suggest that you do both options. Keep your server running and associate an elastic IP. That way if you do need to reboot it for some reason, you will still keep the same IP address, and it doesn't cost you anything more either way."

"Note that your elastic IP address is allocated until you release it, not until you terminate your instance. So make sure you release it when you no longer need it. Otherwise you will get a nasty $3 bill every month."

I did both.

# Domain Names and IP Addresses
Domain names make it easy for humans to reference IP addresses. \(Instead of typing the IP address into the search bar, you type a domain name\).
To find the IP address a domain name references, use the `dig` command:
`dig [domain name]`

When connecting to another device, you hop across the network to reach it. The route is dynamically calculated each time you connect.
Use `traceroute` to see each router you connect to on the way.
`traceroute [domain name]`

"You can get information about a domain name from the domain name registry using the `whois` console utility."
`whois byu.edu`

# CSS Notes
## 3 Ways to impliment CSS
1. Use the style attribute of an HTML element and explicitly assign one or more declarations.

Ex: `<p style="color:green">CSS</p>`

2. Use the HTML style element to define CSS rules within the HTML document. The style element should appear in the head element of the document so that the rules apply to all elements of the document.

Ex:
```html
<head>
  <style>
    p {
      color: green;
    }
  </style>
</head>
```

3. Use the HTML link element to create a hyperlink reference to an external file containing CSS rules. The link element must appear in the head element of the document.

Ex:
    HTML
    ```html
    <link rel="stylesheet" href="styles.css" />
    ```

    styles.css
    ```css
    p {
      color: green;
    }
    ```

***All of the above examples are equivalent, but using the `link` element usually is the preferred way to define CSS.\*\*\*

## The CSS Box Model:
- Everything is defined as boxes
- Styles are applied to different regions of the box. (regions are boxes within boxes)
- The innermost box holds the element's content. (text, image, etc. of an element is displayed)
- Next is padding. (Inhherits things like background color)
- After padding is the border. (Has thickness, line style, and color)
- Margin is the final outer box. ("The margin is considered external to the actual styling of the box and therefore only represents whitespace")

## Things to be aware of:
-  Any declaration property defined at a lower level will override the higher declaration. (Most recent rule overwrites older rules. rules at the bottom of the page overwrite rules at the top)
-  "By default, the width and height of an element is defined by the width and height of the content box. You can change the box-sizing CSS property from the default value of content-box to border-box in order to redefine the width and height to also include the padding and the border. This often makes it easier to style elements when their visual size matches their actual size."

## Selectors
- You "select" an HTML element and apply declarations to it to change aspects of how it's displayed.
- Selecting `body` will cascade our declaration down to all the children of the body, which is the whole document. This can also be done by using the `*` wildcard element name selector to select all elements.

## Combinators
Combinators allow you to further specify what elements you want changed.

| Combinator | Meaning	| Example | Description|
| --- | --- | --- | --- |
| Descendant | A list of descendants | `body section` |	Any section that is a descendant of a body |
| Child |	A list of direct children |	`section > p`	| Any p that is a direct child of a section|
|General sibling |	A list of siblings | `div ~ p` |	Any p that has a div sibling|
|Adjacent sibling |	A list of adjacent siblings |	`div + p`	| Any p that has an adjacent div sibling|

Adjacent sibling = Have same parent. Comes immediatly after the first element.

Ex:
HTML:
```html
<div>
  <h1>Heading</h1>
  <p>Paragraph 1</p>
  <p>Paragraph 2</p>
</div>
```
CSS:
```css
h1 + p {
  color: orange;
}
```
This would make any `p` element the color orange if it immediatly follows an `h1` element. So in this case, paragraph 1 would be orange.

## Class and ID selectors
Ex:
```html
<body>
  <h1>Departments</h1>
  <p>welcome message</p>
  <section id="physics">
    <h2>Physics</h2>
    <p class="introduction">Introduction</p>
    <p>Text</p>
    <p class="summary">Summary</p>
  </section>
  <section id="chemistry">
    <h2>Chemistry</h2>
    <p class="introduction">Introduction</p>
    <p>Text</p>
    <p class="summary">Summary</p>
  </section>
</body>
```
Classes can include multiple elements. Use `.[classname]`. Combine with element to target specific types `[element].[classname]`

Ex:
Affect whole class:
```css
.summary {
  font-weight: bold;
}
```
Affect certain type of element in a class
```css
p.summary {
  font-weight: bold;
}
```
ID specifies a specific element. Only one element can have that ID. (multiple elements can't have the same ID). Use `#[idname]`.

Ex:
```css
#physics {
  border-left: solid 1em purple;
}
```
## Attribute Selector:
- allow you to select elements based upon their attributes.
- You can use an attribute selector to select any element with a given attribute
- You can also specify a required value for an attribute
- Attribute selectors also support wildcards such as the ability to select attribute values containing specific text (p[href*="https://"]).

Ex:
Select Attribute
```css
p[class] {
  color: red;
}
```
Select attribute with specific value
```css
p[class='summary'] {
  color: red;
}
```
Select attr that includes partial value
```css
p[class*="sum"] {
  color: red;
}
```

`*=` --> contains substring

`^=` --> starts with substring

`$=` --> ends with substring

## Pseudo Selector:
CSS also defines a significant list of pseudo selectors which select based on positional relationships, mouse interactions, hyperlink visitation states, and attributes.

Ex:
```css
section:hover {
  border-left: solid 1em purple;
}
```

## Declarations:
List of some basic delcarations:
| Property | Value | Example | Discussion| 
|---|---|---|---|
background-color | color | red | Fill the background color
border | color width style | #fad solid medium | Sets the border using shorthand where any or all of the values may be provided
border-radius | unit | 50% | The size of the border radius
box-shadow | x-offset y-offset blu-radius color	| 2px 2px 2px gray | Creates a shadow
columns	| number | 3 | Number of textual columns
column-rule	| color width style	| black thin solid | Sets the border used between columns using border shorthand
color	| color	| rgb(128, 0, 0) | Sets the text color
cursor | type	| grab | Sets the cursor to display when hovering over the element
display | type | none | Defines how to display the element and its children
filter	| filter-function	| grayscale(30%)	| Applies a visual filter
float	| direction | right	| Places the element to the left or right in the flow
flex |   |   | Flex layout. Used for responsive design
font	| family size style	| Arial 1.2em bold | Defines the text font using shorthand
grid | 			| Grid layout. | Used for responsive design
height	| unit	| .25em	| Sets the height of the box
margin	| unit	| 5px 5px 0 0	| Sets the margin spacing
max-[width/height]	| unit	| 20%	| Restricts the width or height to no more than the unit
min-[width/height]	| unit	| 10vh	| Restricts the width or height to no less than the unit
opacity | number | .9 | Sets how opaque the element is
overflow	| [visible/hidden/scroll/auto]	| scroll	| Defines what happens when the content does not fix in its box
position	| [static/relative/absolute/sticky]	| absolute	| Defines how the element is positioned in the document
padding | unit	| 1em 2em	| Sets the padding spacing
left	| unit	| 10rem	| The horizontal value of a positioned element
text-align	| [start/end/center/justify]	| end	| Defines how the text is aligned in the element
top	| unit	| 50px	| The vertical value of a positioned element
transform	| transform-function	| rotate(0.5turn)	| Applies a transformation to the element
width	| unit	| 25vmin	| Sets the width of the box
z-index	| number	| 100	| Controls the positioning of the element on the z axis

List of units
| Unit | Description |
|---|---|
px	| The number of pixels
pt	| The number of points (1/72 of an inch)
in	| The number of inches
cm	| The number of centimeters
%	  | A percentage of the parent element
em	| A multiplier of the width of the letter m in the parent's font
rem	| A multiplier of the width of the letter m in the root's font
ex	| A multiplier of the height of the element's font
vw	| A percentage of the viewport's width
vh	| A percentage of the viewport's height
vmin	| A percentage of the viewport's smaller dimension
vmax	| A percentage of the viewport's larger dimension

Ways of Describing Colors
|Method | Example	| Description |
|---|---|---|
keyword	| red	| A set of predefined colors (e.g. white, cornflowerblue, darkslateblue)
RGB hex | #00FFAA22 or #0FA2 | Red, green, and blue as a hexadecimal number, with an optional alpha opacity
RGB function | rgb(128, 255, 128, 0.5) | Red, green, and blue as a percentage or number between 0 and 255, with an optional alpha opacity percentage
HSL	| hsl(180, 30%, 90%, 0.5)	| Hue, saturation, and light, with an optional opacity percentage. Hue is the position on the 365 degree color wheel (red is 0 and 255). Saturation is how gray the color is, and light is how bright the color is.

## Fonts
`font-family` property represents and ordered list of fonts. By default first one is selected. First may differ dependng on operating system.
4 major font families = Serif, sans-serif, fixed, and symbol
- A serif is a small stroke attached to the ends of a character's major strokes. These fonts have extra strokes.
- Sans-serif fonts do not have extra strokes.
- Fixed fonts characters all are the same size.
- Symbol fonts represent non-language characters such as arrows or emojis

To import fonts use `@font-face` and provide font name and source location

Ex:
```css
@font-face {
  font-family: 'Quicksand';
  src: url('https://cs260.click/fonts/quicksand.ttf');
}

p {
  font-family: Quicksand;
}
```
If you do not want to host font files on your server, then you can load them from a font provider.
- Google provides a large selection of open source fonts that you can use without paying any royalties. The easiest way to use Google fonts is to use a CSS import statement to reference the Google Font Service. This will automatically generate the CSS for importing the font.
  - Ex:
    ```css
    @import url('https://fonts.googleapis.com/css2?family=Rubik Microbe&display=swap');

    p {
      font-family: 'Rubik Microbe';
    }
    ```

## Animations
Make animations using the `animation` property and defining `keyframes`.

Ex:
```css
p {
  text-align: center;
  font-size: 20vh;

  animation-name: demo;
  animation-duration: 3s;
}

@keyframes demo {
  from {
    font-size: 0vh;
  }

  95% {
    font-size: 21vh;
  }

  to {
    font-size: 20vh;
  }
}
```
`animation-name` --> let's us specifiy what keyframe to look at for the animation

`animation-duration` --> how long the animation should be

`@keyframes [keyframe name]` --> let's us define what a keyframe should do. (Think of it like a function in programming)

`[x]% {}` --> define what should happen at x% of the way through the animation. (example above shows 95% {})

# HTML
HTML = Hyper Tet Markup Language
SPA = Single Page Application
MPA = Multi-Page Application

HTML defines a header (<!DOCTYPE html>) that tells the browser the type and version of the document. You should always include this at the top of the HTML file.

Attributes:
- Can use single or double quotes ('' or "")

## Common Elements:
| element	| meaning |
|---|---|
html	| The page container
head	| Header information
title	| Title of the page
meta	| Metadata for the page such as character set or viewport settings
script	| JavaScript reference. Either a external reference, or inline
include	| External content reference
body	| The entire content body of the page
header	| Header of the main content
footer	| Footer of the main content
nav	| Navigational inputs
main	| Main content of the page
section	| A section of the main content
aside	| Aside content from the main content
div	| A block division of content
span	| An inline span of content
h<1-9>	| Text heading. From h1, the highest level, down to h9, the lowest level
p	| A paragraph of text
b	| Bring attention (bold)
table	| Table
tr	| Table row
th	| Table header
td	| Table data
ol,ul	| Ordered or unordered list
li	| List item
a	| Anchor the text to a hyperlink
img	| Graphical image reference
dialog	| Interactive component such as a confirmation
form	| A collection of user input
input	| User input field
audio	| Audio content
video	| Video content
svg	| Scalable vector graphic content
iframe	| Inline frame of another HTML page

Use `<!--[text]-->` in order to mak comments in HTML.

## HTML Input Elements
<ins>Common HTML Elements That Accept Inputs</ins>
Element | Meaning	| Example
|---|---|---|
form	| Input container and submission	| <form action="form.html" method="post">
fieldset	| Labeled input grouping	| <fieldset> ... </fieldset>
input	| Multiple types of user input	| <input type="" />
select	| Selection dropdown	| <select><option>1</option></select>
optgroup	| Grouped selection dropdown	| <optgroup><option>1</option></optgroup>
option	| Selection option	| <option selected>option2</option>
textarea	| Multiline text input	| <textarea></textarea>
label	| Individual input label	| <label for="range">Range: </label>
output	| Output of input	| <output for="range">0</output>
meter	| Display value with a known range	| <meter min="0" max="100" value="50"></meter>

`form` used to be the only way for the browser to send input data to a web server. Javscript allows us to use input data without sending it to the web server. `form` is often used as a container now because of this.

## HTML Input Element (different from Input Elements above)
The input element represents many different input types. You set the type of input with the type attribute along with any other attribute associated with that specific input.

<ins>List of Input Element Types</ins>
Type	| Meaning
|---|---|
text	| Single line textual value
password	| Obscured password
email	| Email address
tel	| Telephone number
url	| URL address
number	| Numerical value
checkbox	| Inclusive selection
radio	| Exclusive selection
range	| Range limited number
date	| Year, month, day
datetime-local	| Date and time
month	| Year, month
week	| Week of year
color	| Color
file	| Local file
submit	| button to trigger form submission

<ins>Common Shared Input Element Attributes</ins>
Attribute	| Meaning
|---|---| 
name | The name of the input. This is submitted as the name of the input if used in a form
disabled | Disables the ability for the user to interact with the input
value	| The initial value of the input
required | Signifies that a value is required in order to be valid

## Data Validation
Several of the input elements have validation built into them.

`required` - Boolean. Setting this attribute makes it so a value is needed in order to be submitted.

Ex:
```css
<div class="group">
  <input type="text" required />
  <label>Required</label>
</div>
```

`pattern` - exists on text, search, url, tel, email, and password inputs. When present, the pattern attribute provides a regular expression that must match for the input to be considered as valid.

Ex:
```css
<input type="text" id="country_code" name="country_code" pattern="[A-Za-z]{3}" title="Three letter country code (e.g., USA)">
```

## Special Characters
Entity Syntax for Common Special Characters
| Character	| Entity |
|---|---|
| & | \&amp; |
| <	| \&lt; |
| >	| \&gt; |
| "	| \&quot; |
| '	| \&apos; |
| 😀	| \&#128512; (unicode example) |

You can also use the entity syntax to represent any unicode character.

By default a web server will display the HTML file named `index.html` if a specific HTML file is not requested by the web browser. This is why it's common to name your main HTML file `index.html`.

Ex: You search for `https://google.com`. It will actually request for `https://google.com/index.html`.

