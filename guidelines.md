This is an abstract of these guidelines http://codeguide.co/



## HTML

* Use soft tabs with two spaces (Sublime Text: https://css-tricks.com/changing-spaces-tabs-sublime-text/)
* Nested elements should be indented with two spaces
* Always use double quotes on attributes
* Don't omit optional closing tags

### Attribute order

HTML attributes should come in this particular order (more readable):

- `class`
- `id`, `name`
- `data-*`
- `src`, `for`, `type`, `href`, `value`
- `title`, `alt`
- `role`, `aria-*`

Example

````html
<header class="header">
  <h1 class="header__title" id="heading">Title 1</h1>
  <a class="header__link" id="link1" data-value="1" title="First link" href="#">Link 1</a>
</header>

````



### HTML tabindex Attribute

For accessibility, we should add the correct `tabindex` on each focusable element.



### Editor preferences

- Use soft-tabs set to two spaces.
- Trim trailing white space on save.
- Set encoding to UTF-8.
- Add new line at end of files.



## BEM

BEM improves maintainability as well as readability but at the beginning it can seem strange as convention.
To avoid big headaches, I believe we can adopt these guidelines https://www.smashingmagazine.com/2016/06/battling-bem-extended-edition-common-problems-and-how-to-avoid-them/

The following table shows elements and meanings

| TYPE             | PREFIX      | EXAMPLES                 |
| ---------------- | ----------- | ------------------------ |
| Component        | `c-`        | `c-card``c-checklist`    |
| Layout module    | `l-`        | `l-grid``l-container`    |
| Helpers          | `h-`        | `h-show``h-hide`         |
| States           | `is-``has-` | `is-visible``has-loaded` |
| JavaScript hooks | `js-`       | `js-tab-switcher`        |



The following snippet of code shows an example of BEM in action:

```scss
<!-- this is a block -->
<div class="c-searchBox">

  <!-- this is an element with a modifier -->
  <input class="c-searchBox__input c-searchBox__input--big" type="text">
  <!-- this is another element with a different modifier -->
  <input class="c-searchBox__input c-searchBox__input--red" type="text">
</div>


// Inside our .scss files we can use the following mixins
// element() or simply e()
// modifier() or simply m()

// The element() mixing is nested inside a block (a CSS class)
// The modifier() mixing should be nested inside an element instead

.c-searchBox {

  // Here we are inside a BLOCK .c-searchBox

  @include element('input') {

    // Here we are inside the input element or .c-searchBox__input

    @include modifier('big') {
      // Here we are inside the modifier of the parent element or .c-searchBox__input--big
    }

    @include modifier('small') {
      // Here we are inside the modifier of the parent element or .c-searchBox__input--small
    }

    @include modifier('red') {
      // Here we are inside the modifier of the parent element or .c-searchBox__input--red
    }

  }

}
```





## Sass Guidelines

For structuring our SASS files we adop the 7 - 1 pattern https://sass-guidelin.es/#architecture

This is the intended structure that we should follow as much as possible:



```
sass/
|
|– abstracts/
|   |– _variables.scss    # Sass Variables
|   |– _functions.scss    # Sass Functions
|   |– _mixins.scss       # Sass Mixins
|   |– _placeholders.scss # Sass Placeholders
|
|– base/
|   |– _reset.scss        # Reset/normalize
|   |– _typography.scss   # Typography rules
|   …                     # Etc.
|
|– components/
|   |– _buttons.scss      # Buttons
|   |– _carousel.scss     # Carousel
|   |– _cover.scss        # Cover
|   |– _dropdown.scss     # Dropdown
|   …                     # Etc.
|
|– layout/
|   |– _navigation.scss   # Navigation
|   |– _grid.scss         # Grid system
|   |– _header.scss       # Header
|   |– _footer.scss       # Footer
|   |– _sidebar.scss      # Sidebar
|   |– _forms.scss        # Forms
|   …                     # Etc.
|
|– pages/
|   |– _home.scss         # Home specific styles
|   |– _contact.scss      # Contact specific styles
|   …                     # Etc.
|
|– themes/
|   |– _theme.scss        # Default theme
|   |– _admin.scss        # Admin theme
|   …                     # Etc.
|
|– vendors/
|   |– _bootstrap.scss    # Bootstrap
|   |– _jquery-ui.scss    # jQuery UI
|   …                     # Etc.
|
`– main.scss              # Main Sass file
```





## GITHUB

The master branch represents the application into production. So, each feature or component must be developed in isolation on a **separate branch**.

When you've done with a feature, you should push your work on the remote repository on its branch:

```
git push origin <your-branch>
```

After that, to go into production, you can create a new pull request directly on GitHub by clicking on the `new pull request` button





