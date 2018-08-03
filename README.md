# pygments-github-css
![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)
[![](https://travis-ci.org/PhilipTrauner/pygments-github-css.svg?branch=master)](https://travis-ci.org/PhilipTrauner/pygments-github-css)

## Usage
Building minified version:
```bash
git clone --depth=1 https://github.com/PhilipTrauner/pygments-github-css
cd pygments-github-css
yarn install
```

Using CDN:
```html
<link rel="stylesheet" href="https://cdn.rawgit.com/PhilipTrauner/pygments-github-css/master/github.css" />
```

## Compromises
Pygments tokens do not map to GitHub tokens cleanly. Certain compromises had to be made to obtain a mapping that closely matches the look of GitHub's highlighter.

**Actions**: ✓ Apply style | ✗ Do not apply style  

|Element|GitHub|Pygments|Solution|
|-------|------|--------|--------|
|`Operator`|Dot (.) is not treated as an operator|Dot (.) is treated as an operator|✗ (because all dots would be colored incorrectly)|
|`Name.Builtin`|Differentiates between builtin functions and types (completely inconsistent)|Does not differentiate|✓|
|`Name.Decorator`|Differentiates between builtin decorators and regular names|Does not differentiate|✓ (regular decorator style)|
|Optional arguments|Differentiates between regular arguments and optional arguments|Does not differentiate|✗|
|`Name.Namespace`|Namespace imports are ignored|Namespace imports are not ignored|✓|
|`Comment.Preproc`|Treated as constants|Special case|✓|
|`Name`|Functions are treated as names in some languages|Functions and variables are names|✗|
|`Comment.Preproc`|Treated differently depending on language (C++: colored, Rust: uncolored, XML: multi-colored, ...)|Treated equally|✓|
|`Name.Attribute`|Frequently treated as text (LaTeX, ...)|Treated specially|✗|
|`Generic.Heading`|"index..." is interpreted as regular text|"index..." is still part of header|✓|
|`Generic.Subheading`|File list is interpreted as regular text|File list is still part of subheading|✓|

### Unmappable tokens
Tokens that I could not find instances of on GitHub:

* `Generic.Emph`: Marks the token value as emphasized.
* `Generic.Error`: Marks the token value as an error message.
* `Generic.Output`: Marks the token value as program output.
* `Generic.Prompt`: Marks the token value as command prompt.
* `Error`: Lexer error 

If you happen to come across a piece of code that contains one of these tokens feel free to create an issue or open up a pull request. Make sure to denote the file extension!
