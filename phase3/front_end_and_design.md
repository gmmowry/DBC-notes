# Front-end & Design Workshop: "How to make things not look like shit"

What is design?
* Aesthetics
* Usability
* Organization

What makes a good site?
* Provides the features you need
* Those features are easy and pleasant to use
* Use Phase 1 and Phase 2 students to test UX; design things assuming everyone is drunk

Usability
* Learnability: how easy is it for users to accomplish basic tasks the first time they come to the site?
* Efficiency: once learners used the design, how quickly can they perform tasks?
* Memorability: when users return to the design after a period of not using it, how easily can they reestablish proficiency? Facebook makes a lot of very small design changes over a long period so users can acclamate 
* Errors: how many errors do they make? are they severe? how easily can they recover from these errors? Important to think about this with Javascript.
* Satisfaction: how pleasant is it to use the design?


Design Matters
* Most design thoughts are based on visceral reactions --> we want neutral if not positive
* Aesthetics:
| Classical | Expressive |
|-----------|-------------|
| Order | Originality |
| Clarity | Creativity |
| Creates trust | Must complement original purpose |
| Usability | Design |
| Reflective | Visceral |

* How do we know what to do?: Patterns and experience, mimicing the real world (buttons look like buttons in the real world)
* Personality: people identify with (or avoid) certain personalities
* Trust is related to personality
* Perception and expectations are linked with personality

# Web Design 101

Layout File
* Bunch of content
* Need to fit it together

Things to think about:
* Need answer to be close to the question, need question to be close to the answer
* Organize elements into related groups
* Alignment: elements can be aligned flush left, centered, or aligned flush right
* Ensure edges of elements line up (EVERYTHING TOUCHES THE MARGINS YAYYY!)
* Adjust the width of an element so it aligns with the others
* Think about the website as a grid/on graph paper: know which row an element is in, know how many columns it is, etc.
* We can use: unsemantic, simple grid, don't overthink it grids
* Huge fonts grab attentions and makes the blog title important - but don't make it too big
* Huge fonts all over make things overwhelming and confusing visual hierarchy
* Large blocks of color draw attention
* White space around an item brings your attention to it

# HTML & CSS Standards
* HTML is for content: choose tags based on the content, list for nav links or lists of data, table only for tabular data
* CSS is for presentation 

HTML Best Practices
* set defaults for font, font size, colors, lists, etc.
* Use wrappers: div or other element that's a container for a content; set width/max-width; center (margin: 0 auto)

HTML5
* not all supported by all browsers
* semantic tags: nav, header, section, article (great for wrappers) - definitely use them!
* metadat: i.e. show address info in search results
* video and audio tags
* canvas tag for dynamic content (w/JS)
* geolocation
* Storage! SessionStorage and LocalStorage

CSS Best Practices
* prefer inline-block over float
* use id as a unique name for element (only one on a page with that id)
* use class everywhere else
* make class reusable as best you can
* horizontal lists are swell

Reset 
* some tags have default styles (based on a browser)
* default styles vary in different browsers and may change
* reset default styles so you can always start from the same place
* Normalize.css --> download and put it in your asset pipeline. it resets all of the styles so you start from the same place in every browser
* Normalize should happen first in the file, so it doesn't overwrite anything and resets things before we style

Psuedo-selectors: action related selectors (hover, before - , after - , et.)

Icon Fonts
* use pseudo elements and @font-face to add icons to site
* Style like text (color, size, etc.)
* Use any styling that you would use on text
* Font Awesome is awesome! fontawesome.github.io/Font-Awesome

SASS/SCSS
* Syntactically Awesome StyleSheets
* makes CSS look more like code
* SASS syntax: whitespace-aware
* SCSS: 100% compatible with CSS
* Example of SCSS:
```ruby
$base-font-size: 16px;
$primary-color: red;
$font-color: gray;
```

Choosing Styles
Font
* Display font for headlines, logo, etc.: large, decorative, use sparingly
* Text font for everything else
* Choose 1 of each or choose a versatile text font
Readability
* base font size at least 16px
ensure the line-height leaves enough space
* Contrast between background and text 
Web Fonts
* before: only use fonts that are installed on the users' computer
* now HMTL5 @font-face - you specify a file for every different font type
* google fonts
Color
* conveys meaning
* makes recognizable
* contrast!
* Colour Lovers website
* Palette Tab Chrome extension
* Choose a primary color for header/buttons/etc.
* Shades of a neutral color - gray, brown (text, nav, etc.)
* Contrast to neutral (background, could be white)
* Matching colors

Visual Styleguide
* Living, breathing styleguide (aka HTML and CSS from real site)
* Replacement for photoshop or images from designer

Process for group project:
* Wireframe: layout, organization, boxes of content, alignment, either use pen&paper or online tool
* create a visual style guide
* Code style guide in Rails: app/assets/stylesheets/base (base.scss and _colors.scss)
* Add page specific styles in page specific SCSS file