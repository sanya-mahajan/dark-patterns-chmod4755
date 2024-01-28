### Dark Patterns
Dark patterns are design patterns that lead users to act in a certain way that is contrary to their interests, exploiting design power unilaterally in the interests of their creator.


## Contents
- [Features](#features)
- [Video and Screenshots](#video-and-screenshots)
- [How it works](#how-it-works)
- [Browser Compatibility](#browser-compatibility)
- [Installation](#installation)
- [Libraries Used](#libraries-used)
- [License](#license)

## Features
- Automatic detection of dark patterns on web pages
- Highlighting of suspicious elements with minimal impact on page appearance
- Popup window providing information on detected dark patterns, including their category and an explanation
- No blocking of web page content
- Extension icon displaying number of detected dark patterns
- Function to individually highlight each detected dark pattern
- Supporting multiple languages (currently English available)

## Video and Screenshots
### Teaser Video
<!-- Videos here -->
### Screenshots
<!-- Screenshots here-->

## How it works
The Pattern Highlighter works entirely locally in the browser and does not connect to any servers. When visiting a web page, the extension injects a small script that creates an internal temporary copy of the entire web page i.e. its HTML DOM. After a short pause (about 1.5 seconds) a second copy is created. Subsequently, all elements of these copies are examined individually and in combination with child elements using the implemented pattern detection methods. The pattern detection methods decide whether an element is a specific dark pattern or not. The reason for creating two copies with a time gap is to detect changes on the web page. This makes it possible to detect certain patterns such as countdowns.

Mainly responsible for the results of the pattern detection are the mentioned detection functions. These are centrally defined in the `patternConfig` object together with information about the associated patterns in [`constants.js`](chrome/scripts/constants.js). This `patternConfig` object can be extended arbitrarily by additional patterns and functions, according to the requirements that are commented in [`constants.js`](chrome/scripts/constants.js).

Currently, one detection function each is implemented for the four following patterns.
- [Countdown]
- [Scarcity]
- [Social Proof]
- [Forced Continuity]

Right now, all of the four detection functions are optimized for German and English websites and cannot be applied to websites in other languages.

## Browser Compatibility
| Browser         	| Is compatible? 	| Tested versions                                                               	|
|-----------------	|:--------------:	|-------------------------------------------------------------------------------	|
| <img src="https://raw.githubusercontent.com/edent/SuperTinyIcons/master/images/svg/chrome.svg" width="24px" style="background: white" /> Google Chrome   	|        ✅       	| <ul><li>113.0.5672.92 (Mac/arm64)</li><li>113.0.5672.93 (Win/x64)</li></ul> 	|
| <img src="https://raw.githubusercontent.com/edent/SuperTinyIcons/master/images/svg/edge.svg" width="24px" style="background: white" /> Microsoft Edge  	|        ✅       	| <ul><li>113.0.1774.35 (Mac/arm64)</li><li>113.0.1774.35 (Win/x64)</li></ul>   	|

### Google Chrome, Microsoft Edge and Opera
The Pattern Highlighter uses an [API](https://developer.chrome.com/docs/extensions/reference/) that is specified by Google and primarily supported by the Google Chrome browser. However, many other browsers also support this Chrome API. Since Microsoft Edge and Opera, just like Google Chrome, are built on the [Chromium](https://en.wikipedia.org/wiki/Chromium_(web_browser)) code base, the [API support](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/Browser_support_for_JavaScript_APIs) of the three browsers is almost completely identical. Consequently, the extension will behave the same way in these browsers. This is also to be expected for other browsers that are based on Chromium.

## Installation
To install the extension, the repository or the `chrome` folder must be downloaded. Since the extension is not loaded from the stores of the browser providers, it must be installed in the developer mode of the browsers. For this, the individual steps for the different tested browsers are listed below.

### Chrome
1. Go to the Extensions page by entering `chrome://extensions` in a new tab.
   - Alternatively, click on the Extensions menu puzzle button and select **Manage Extensions** at the bottom of the menu.
   - Or, click the Chrome menu, hover over **More Tools**, then select **Extensions**.
2. Enable Developer Mode by clicking the toggle switch next to **Developer mode**.
3. Click the **Load unpacked** button and select the `chrome` directory.
4. (Optional): Click the Extensions menu puzzle button in the address bar and then click the **Pin** button next to the *Pattern Highlighter* to keep its icon permanently displayed.

