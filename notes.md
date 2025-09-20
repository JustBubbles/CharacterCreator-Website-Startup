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
```
<head>
  <style>
    p {
      color: green;
    }
  </style>
</head>
```

3. Use the HTML link element to create a hyperlink reference to an external file containing CSS rules. The link element must appear in the head element of the document.
Ex:`<link rel="stylesheet" href="styles.css" />`
    styles.css
    ```
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
```
HTML:
<div>
  <h1>Heading</h1>
  <p>Paragraph 1</p>
  <p>Paragraph 2</p>
</div>

CSS:
h1 + p {
  color: orange;
}
```
This would make any `p` element the color orange if it immediatly follows an `h1` element. So in this case, paragraph 1 would be orange.

## Class and ID selectors
Ex:
```
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
```
Affect whole class
.summary {
  font-weight: bold;
}

Affect certain type of element in a class
p.summary {
  font-weight: bold;
}
```
ID specifies a specific element. Only one element can have that ID. (multiple elements can't have the same ID). Use `#[idname]`.
Ex:
```
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
```
Select Attribute
p[class] {
  color: red;
}

Select attribute with specific value
p[class='summary'] {
  color: red;
}

Select attr that includes partial value
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
```
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
px	The number of pixels
pt	The number of points (1/72 of an inch)
in	The number of inches
cm	The number of centimeters
%	A percentage of the parent element
em	A multiplier of the width of the letter m in the parent's font
rem	A multiplier of the width of the letter m in the root's font
ex	A multiplier of the height of the element's font
vw	A percentage of the viewport's width
vh	A percentage of the viewport's height
vmin	A percentage of the viewport's smaller dimension
vmax	A percentage of the viewport's larger dimension
