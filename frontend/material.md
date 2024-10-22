![material-components-selection](https://github.com/user-attachments/assets/1ae41631-d7f0-476c-bb64-d12f62699dd8)

# Introduction to Material 3

Material 3 is the current design language used in Android 14, Android's latest release version. To design in Material 3 effectively, it is extremely important to understand the intricacies of Material 3 and how it *intends* developers to design using its components. Google has developed a [great website for Material 3](https://m3.material.io) that discusses the components within Material design, how color schemes and themes work, typography, layout, and more. CSS can be annoying at times, but good user interface design is *extremely* important for software engineers to appreciate. When non-developers (users) go to a website or use a web application, they may not appreciate the intricacies of the website's backend or dev ops setup, but *everyone* appreciates a good design. In fact, design can make or break an application. Developers must pay close attention to design decisions. It is not something to be rushed or brushed aside, as user interface design makes up a significant part of the overall user experience.

Developers might be concerned that they do not know anything about design or have a good eye with colors. However, you do not have to be. The point of a cohesive design system such as Material is to provide all of these tools, rules, and conventions for you. The job of the developer is just to understand how they work, and apply the design system according to its conventions.

When you are developing your own apps in the future, you will have to choose a design system to conform to. If you are experienced in UI/UX design, you may choose to design your own - however, it is far more likely that you adopt an existing design system. If you are developing for Android, you will likely choose Material. Apple has their own design system for Apple platforms, and there are many design systems for web. Angular works best with Angular Material, which is why our site uses Material. 

## Components

The Material Design system has many UI elements, known as components, that are the building blocks for a UI made with Material design. There are many components, all of which are catalogued [here](https://m3.material.io/components). There are many components, all of which are best by the official docs. I recommend scrolling through all of these just to be aware of the different components that Material offers!

In addition, a terrific resource is the [Official Material 3 Design Kit](https://www.figma.com/community/file/1035203688168086460) on Figma. This kit contains all of the different Material components and is a great resource for designing UI layouts.

Most components from Material 3 are available in Angular Material, but to find out more about specific implementation details, check out the [official documentation](https://material.angular.io/components/categories). 

# Material Theme for the CSXL Site

The styling of an application using Material 3 (M3) depends on the selected *theme*. M3 themes contain the color palette and fonts that enable developers to customize M3 to their site's brand while still following all M3 guidelines and be able to effectively use M3 components. The M3 color system has been thoroughly researched by UI/UX engineers at Google and define the framework for how components and elements in an app should be colored to maximize usability and accessibility (for those with sensory or visual disabilities). In order to effectively utilize M3, it is very important to familiarize yourself with the M3 color system and the terminology used. 

## The Color System

### Color Palette

The M3 color system is defined through a *color palette*. M3 algorithmically generates color palettes based on a single source color.

Please read [the following explanation on Material 3's website](https://m3.material.io/styles/color/system/how-the-system-works#10dccd89-5358-410d-9198-3a6bd0ace2c0), as their explanation explains the process the best. In short, this process generates *five key colors:*

- Primary
- Secondary
- Tertiary
- Neutral
- Neutral Variant

You will see these terms thrown around a lot in the new CSXL site upgrade, both in the names of CSS classes and options as parameters to Material components.

Palettes of different hues are then created from each of these generated colors, and these colors are assigned to **roles**. These roles define the basis for the entire M3 color scheme. See the [official diagram](https://m3.material.io/styles/color/system/how-the-system-works#7e1088b5-2667-4bf1-b731-cb7eb290babe) to see how different hues of the five key colors creates different colors for many roles.

In the CSXL site, we use Material's purple as our primary color instead of the green shown here. This is the same color scheme used on the official documentation page. 

**Below** are the color palettes and roles used in the new CSXL site:

<img width="1263" alt="Screenshot 2024-07-23 at 11 41 20 AM" src="https://github.com/user-attachments/assets/8c67a284-994d-4965-804b-e91989a88971">

These colors were generated by Material 3's algorithms. You can access the **theme generator [here](https://material-foundation.github.io/material-theme-builder/)**, which was used to generate the theme for the CSXL site. Try out different options to play around with how colors are generated!

### Color Roles

You will notice some common phrasing amongst the generated color roles. Here are the descriptions of each color role according to M3:

* **Surface** – A role used for backgrounds and large, low-emphasis areas of the screen.
* **Primary, Secondary, Tertiary** – Accent color roles used to emphasize or de-emphasize foreground elements.
* **Container** – Roles used as a fill color for foreground elements like buttons. They should not be used for text or icons.
* **On** – Roles starting with this term indicate a color for text or icons on top of its paired parent color. For example, on primary is used for text and icons against the primary fill color.
* **Variant** – Roles ending with this term offer a lower emphasis alternative to its non-variant pair. For example, outline variant is a less emphasized version of the outline color.

I *highly* recommend checking out the [official documentation on color roles and how to use them](https://m3.material.io/styles/color/roles#19e75989-7485-4f5b-a769-940c4e4364bc). There are a lot of do-s and don't-s with how to use color roles and how to combine them. To design in accordance with M3, it is important to learn the rules behind using and combining colors so that you can take full advantage of the design system M3 has created for us.

## The Typography System

Material themes also include a typography system, which bundles together fonts. Vanilla M3 uses Google's **[Roboto](https://fonts.google.com/specimen/Roboto)** font, which is what the CSXL site uses also.

### Type Scales

You might be wondering about font sizes and weights, and M3 has us covered for this too. M3 includes what are known as *type scales*, which are essentially "font roles" that contain varying font parameters (including size and weight). Learn more about the different type scales [here](https://m3.material.io/styles/typography/type-scale-tokens#425022ff-21dd-4fbe-9eca-9690d0fc8b16).

Each type scale, just like its color role counterpart, have their own intended purposes and use cases. M3 provides guidelines for how these type scales should be used. Sometimes, M3 automatically sets the most appropriate type scales for their own components (such as in `<mat-card-title>`, however other times, further customization is needed.

I recommend checking out the [official type scale usage guide](https://m3.material.io/styles/typography/applying-type) on M3's website, as the website provides many great examples and an in-depth explanation for each category of type scale.

# Adopting The Material 3 Theme

From above, you know that a material theme consists of two components: (1) *colors* and (2) *typography*. Since we are using the standard typography in our theme, we can leave it to the Material defaults.

As mentioned before, I used the **theme generator [here](https://material-foundation.github.io/material-theme-builder/)** to determine the color palettes for the key colors (primary, secondary, tertiary, neutral, and neutral variant). The hex codes for the hues of each of these colors can then be combined into our theme.

## Creating the Theme in `theme.scss`

Material 3 uses **Sass** (file extension `.scss`) files to define its styling. Sass adds different features like methods and variables to traditional CSS. Under the hood, Angular Material is built on Sass files. To define our theme, I created a `theme.scss` file in the `/styles` directory (accessible [here](https://github.com/unc-csxl/csxl.unc.edu/blob/main/frontend/src/styles/theme.scss)).

Variables in Sass are defined starting with a `$` symbol. Check out the `$_palettes` variable [here](https://github.com/unc-csxl/csxl.unc.edu/blob/21a0db56ba247ef930555383ef524beffd6c996a/frontend/src/styles/theme.scss#L34C1-L57C17). This variable attaches the key color (ex: `primary`) and hue number `0-100` to a hex value. This hex value comes directly from the Material Theme Builder. These color codes are also accessible on the Figma. Adding all of the colors here defines the color palette for our M3 theme to use.

Note the use of the special function `_estimate-hue()` used for some styles, including [here](https://github.com/unc-csxl/csxl.unc.edu/blob/21a0db56ba247ef930555383ef524beffd6c996a/frontend/src/styles/theme.scss#L107C8-L107C21). This is due to a bug currently in the Angular Material production release. M3 expects a few more colors than what is provided from the Material 3 theme builder that are not properly generated by the Angular Material package. So, I took the `_estimate-hue()` function from within the Angular Material source code and re-applied it here to generate the colors for hues not provided by either the theme builder or Angular Material's color-creation algorithms. Estimate hue generates a color between two reference colors. For example, the call `_estimate-hue($_neutral_hues, 4, 0, 10)` estimates the color for hue `4` given the reference hues `0` on the dark end and `100` on the lighter end.

At the bottom of the file [here](https://github.com/unc-csxl/csxl.unc.edu/blob/21a0db56ba247ef930555383ef524beffd6c996a/frontend/src/styles/theme.scss#L165-L178), the code gets a bit more readable:

```scss
$light-theme: mat.define-theme((
  color: (
    theme-type: light,
    primary: $_primary,
    tertiary: $_tertiary
  )
));
$dark-theme: mat.define-theme((
  color: (
    theme-type: dark,
    primary: $_primary,
    tertiary: $_tertiary
  )
));
```

This is where we actually *define* the M3 theme using the `mat.define-theme()` function imported at the top of the file. This bundles together our palettes - tertiary, and primary (which contains the rest of the key colors). Notice that there are **two** themes - Angular Material requires the specification of two different themes for light and dark mode! By using the `theme-type` property, Angular Material does the rest of the work for us in terms of matching the correct color roles to the right hues (at this mapping is different depending on light or dark appearance).

The themes have been generated - stored in `$light-theme` and `$dark-theme` respectively. Now, the final step is to apply these themes.

## Implementation of Global Styling through SCSS (`styles.scss`)

The application of these themes, as well as *any custom styling using material theme variables*, is done globally via the `styles/styles.scss` file [here](https://github.com/unc-csxl/csxl.unc.edu/blob/main/frontend/src/styles/styles.scss).

Applying the base theme is relatively simple. We imported the theme into this `styles.scss` file as `csxl-theme`, so the theme can be applied to all components [like so](https://github.com/unc-csxl/csxl.unc.edu/blob/21a0db56ba247ef930555383ef524beffd6c996a/frontend/src/styles/styles.scss#L415-L427):

```scss
/** Apply themes and custom styling to the site. */

html {

    @include mat.all-component-themes(csxl-theme.$dark-theme); /* HERE!*/
    @include apply-styles(csxl-theme.$dark-theme);
    @include apply-overrided-dark-mode-styles(csxl-theme.$dark-theme); /* HERE!*/

    @media (prefers-color-scheme: light) {
        @include mat.all-component-colors(csxl-theme.$light-theme); /* HERE!*/
        @include apply-styles(csxl-theme.$light-theme);
    }
}
```

Notice the lines marked with the comment `/* HERE!*/`. These lines use built-in material functions to apply the theme to the entire file, which we apply in the `html` selector. The `@include` keyword indicates that we want to *include* the CSS output of these functions in our overall CSS file. Using typical CSS, we apply dark mode first. Then, when the color scheme is switched to light mode, we can apply the light mode styles instead.

Notice the one function not called from the `mat` package - `apply-styles()`.

When using Material 3, there are many times we might want to do the following:
* **Use material-specific values to style elements, including color roles and font type scales:** We cannot do this normally from our CSS, since all of the styling files that Angular reads per component are `.css`, not `.scss` files. By not using `.scss`, we lose the ability to call functions or reference our theme variable, rendering us unable to access the colors that we chose.
* **Define global styles for Material:** We may want to create certain CSS classes that help to "bridge the gaps" of Angular Material. For example, Google's M3 defines buttons that use the *primary*, *secondary*, and *tertiary* background colors, but this is unable to be done currently through vanilla Angular Material. We want to create a *global* style class called `.tertiary-button` that properly styles all buttons we want to be tertiary.

Both of these features require the use of our `.scss` files, since they all depend on styling from Material 3. The workaround currently is through **creating the `apply-styles()` *mixin*** (you will see SCSS call such functions mixins).

Take a look at [the following](https://github.com/unc-csxl/csxl.unc.edu/blob/21a0db56ba247ef930555383ef524beffd6c996a/frontend/src/styles/styles.scss#L389C1-L404C2):

```scss
/// Defines a mixin that applies all of the custom style mixins declared above.
/// This mixin is defined so that these @include lines are not duplicated between
/// light and dark mode.
@mixin apply-styles($theme) {
    @include mat-button-styles($theme);
    @include mat-card-styles($theme);
    @include mat-navigation-styles($theme);
    @include mat-list-styles($theme);
    @include mat-header-styles($theme);
    @include mat-icon-styles($theme);
    @include mat-switch-styles($theme);
    @include mat-text-field-styles($theme);
    @include font-styles($theme);
    @include widget-styles($theme);
    @include global-styles($theme);
}
```

The `apply-styles()` mixin / function takes in a theme as a parameter, and inside of it, calls a bunch of other mixins (defined above in the file). These mixins apply specific global styles and define certain classes that allow us to use the features (colors and typography) of Material 3. Taking a theme as a parameter also helps us not duplicate this code between the light and dark mode declarations.

Take a look at an excerpt of the `global-styles` mixin [here](https://github.com/unc-csxl/csxl.unc.edu/blob/21a0db56ba247ef930555383ef524beffd6c996a/frontend/src/styles/styles.scss#L14-L38):

```scss
/** Custom Material Component Styling Mixins */
// Note: These are sorted in alphabetical oder.


/// Defines a mixin that applies global styles using the M3 theme
/// to better conform to Material 3 standards.
/// 
/// @param {theme} $theme: Angular Material theme to apply styles with.
@mixin global-styles($theme) {
    p {
        font: mat.get-theme-typography($theme, body-medium, font);
    }


    .primary-background {
        background: mat.get-theme-color($theme, primary) !important;
        color: mat.get-theme-color($theme, on-primary) !important;
    }


    .primary-background-color {
        background-color: mat.get-theme-color($theme, primary) !important;
        color: mat.get-theme-color($theme, on-primary) !important;
    }
    ...
}
```

This code does both things here. In the `p` CSS selector, a global style is applied, setting all paragraph text to use the `body-medium` type scale, as recommended by Material 3 guidelines. Below, `.primary-background-color` creates a global style that sets the background color of any element with this class to be the `primary` color from the Material palette, with the text color set to `on-primary`. The `!important` flag is commonly used to overwrite settings Material already sets, if needed. These styles can then be used from anywhere in the codebase.

Notice that `mat.get-theme-typography()` and `mat.get-theme-color()` are the two functions used to retrieve the type scales and colors, respectively, from the theme. If you wish to define your own global styles, you will need to use these calls.

To keep things organized, I created mixins by component type to separate applied styles. All of these mixins are also fully documented with a description and descriptions on the inputs / parameters (must usually just the material 3 theme).


## Custom Widgets (`<mat-pane>` and `<search-bar>`)

There are some Material components specified in M3 that Angular Material has not implemented yet. Namely, this is the pane (which is used for backgrounds) and the search bar. I went ahead and created custom components for these, called `<mat-pane>` and `<search-bar>` respectively. Panes are wrappers that contain the same contents that cards would use. Therefore, an ideal setup for a pane would be:

```html
<mat-pane>
  <mat-card-header>
    <mat-card-title>Meaningful Title</mat-card-title>
  </mat-card-header>
  <mat-card-content>
    ...
  </mat-card-content>
  <mat-card-actions>
     <button mat-flat-button>Some Action</button>
  </mat-card-actions>
</mat-pane>
```

More custom widgets will be made and will be written about in a future section!

# Conclusion

I hope this was helpful in understanding how Material 3 works and how global styling has been set up for the site! To learn more, please check out the entirety of the [official M3 docs](https://m3.material.io), which contain a *lot* of good information!
