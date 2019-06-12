# r-sandbox
R sandboxes and teacher pages for in-class and quiz exercises. You can preview the pages at https://adamblake.github.io/r-sandbox. Read the below documentation for setting up your own copy and customizing it.

# Using these sandboxes

It is recommended that you *Fork* this repository before using the pages in it. Using the below instructions, you should be able to get setup in just a few minutes.

## 1. Create a GitHub Account

If you don't have a GitHub account, you will need to create one in order to take advantage of GitHub Pages, which lets you host static webpages. You can create an account at the [GitHub signup page](https://github.com/join).

## 2. Fork this repository

Click the *Fork* button at the top of this page. Once your fork the repository, any changes you make to your fork will not affect this repository. This lets you add or change anything you like without fear of changing things for others. (If you think we should change something, submit a Pull Request: [Creating a Pull Request](https://help.github.com/en/articles/creating-a-pull-request)).

## 3. Setup GitHub Pages for your forked repository

[GitHub Pages](https://pages.github.com/) is designed to host your personal, organization, or project pages from a GitHub repository. To set this up for your fork of this repository, head to your fork, click *Settings* at the top, and scroll down to GitHub Pages. Change the *Source* option to `master`.

## Mostly there!

At this point your sandboxes should be usable with default configurations. You can access tem at `[your username].github.io/r-sandbox/class-sandbox.html` and `[your username].github.io/r-sandbox/quiz-sandbox.html`. For example, Adam Blake's GitHub username is `adamblake` and you can visit his sandboxes at [adamblake.github.io/r-sandbox/class-sandbox.html](https://adamblake.github.io/r-sandbox/class-sandbox.html) and [adamblake.github.io/r-sandbox/quiz-sandbox.html](https://adamblake.github.io/r-sandbox/quiz-sandbox.html). 

The next couple of steps will show you how to customize the sanboxes and setup a nice dashboard to use during class.

## 4. Customizing Sandbox Content

To configure the settings for your DataCamp R sandboxes, you will be editing a simple text file in what is called YAML markup. This is a type of configuration file that is designed to be easy and intuitive for humans to understand (well, at least easy relative to other configuration types...). Generally speaking, you will want to change values in this file in-place *without* changing the format, *especially the indentations.* If you are viewing this README on GitHub, you should see `_config.yml` in the file list at the top of this page. You can edit that file through GitHub and it will update your sandbox webpages automatically.

In `_config.yml` you should see a section that looks like this:

```
sandbox:
  class:
    lang: r
    height: 350
    pre-exercise-code: |
      require(readr)
      require(mosaic)
      require(supernova)
      require(lsr)
    sample-code: null
    hint: null
  quiz:
    lang: r
    height: 350
    pre-exercise-code: |
      require(readr)
      require(mosaic)
      require(supernova)
      require(lsr)
    sample-code: null
    hint: null
```

To break this down, we are looking at the `sandbox` key that has `class` and `quiz` subkeys. Changing settings in the `class` subkey will change the class sandbox, and likewise for the `quiz` subkey. Within each of the subkeys there are a number of settings that can be updated, though mostly you will only be changing `pre-exercise-code`. Here are descriptions of all of the settings:

  - __lang__: What language should this sandbox use. The available options are `r` or `python`. 
  - __height__: This is the height in pixels of the sandbox module. 350 is the default, though this is something you might want to play around with if you feel that there is not enough vertical space. (Note that the width is not as easily configured.)
  - __pre-exercise-code__: This is the R code that will be run invisibly just before the module is loaded for students. Anything you type in this setting will be evaluated as R code. By default, only a few R packages are loaded that are used throughout the course. __Note__: you must use the `|` character like in the example above and the default settings. The `|` tells YAML to consider the next few lines to all be read as a multiline block and not individual settings.
  - __sample-code__: This is the R code that will be pre-populated into the sandbox when the module loads. The code is not automatically run, it's just a placeholder for when the page loads. By default it is set to `null` so as not to display anything. __Note__: if you want to use this setting, you must use the `|` character like in the `pre-exercise-code` setting above. The `|` tells YAML to consider the next few lines to all be read as a multiline block and not individual settings.
  - __hint__: This is text (or HTML markup) that is displayed when users click a "Hint" button on the module. If it is set to `null`, the button will not be displayed.

## 5. Customizing the Class Dashboard

The last thing that you can customize is arguably the coolest (argued by me, [Adam](https://github.com/adamblake)): the in-class dashboard. This dashboard is set up to work with 
 
 - [Poll Everywhere](https://polleverywhere.com) to conduct polls and in-class mini-quizzes (similar to iClicker software, but better),
 - a Google Form we call Ask For Me! that shy students can anonymously type their questions into for a TA or instructor to read,
 - the class sandbox (as configured above),
 - and [Padlet](https://padlet.com) for you and students to share code, images, plots, etc. in class (these can be moderated).
 
For each of these services to work you will need to set them up (maybe 1-2 min each).

### Poll Everywhere

Sign-up at https://polleverywhere.com, then update your `_config.yml` file here with the link to your poll page. For example, if your username is `silly_cactus` your `_config.yml` should have these lines in it:

```
polleverywhere:
  url: https://polleverywhere.com/silly_cactus
```

When you create a poll, this part of the class dashboard will automatically be updated to make the poll visible to students.

### Padlet

Sign-up at https://padlet.com, create a Padlet, then update your `_config.yml` file here with the link to your Padlet. For example:

```
padlet:
  url: [link to padlet here]
```

### Google Form

Create a form at https://docs.google.com/forms/. Once the form is created, click the eye icon in the top right to preview the form. Copy the link in the address bar and add it to your `_config.yml`. If you would like to use the Google styles for the form, mark `use_custom_form` as `false`, otherwise set it to `true`. For example:
```
askforme:
  url: [long google form link here, should end in "viewform"]
  use_custom_form: true
```

Leave the other two subkeys `form_id` and `text_input_name` as `null` unless you know what they mean. When you load the class dashboard after adding the URL, there will be a tool that finds the values for those keys and gives you the settings to copy and paste back into `_config.yml`.
 
## Done! 

That's it! You can now navigate to `[your-username].github.io/r-sandbox` to view a menu, and `[your-username].github.io/r-sandbox/quiz-sandbox`, `[your-username].github.io/r-sandbox/class-sandbox`, `[your-username].github.io/r-sandbox/quiz-sandbox`. for the sub pages.

# Advanced Customizations

Assuming you have already set up your pages and tried them out, there may be things that you want to change about them. This could be as simple as the look and feel (e.g. background colors) or more complex changes to the structure and content (e.g. a special CSS media quer for tablets). For the simple changes to the structure, you can try editing the `*.html` files at the root of the repository, the `*.scss` files in the `styles` directory, or the layout file `default.html` in the `_layouts` directory. 

You may notice that the HTML files contain more than standard HTML markup. In fact, GitHub Pages allows us to use an augmented type of HTML called [Liquid Templating](https://shopify.github.io/liquid/). If you have ever used Twig, Liquid is very similar. Essentially, we can access and print variables using `{{ variable_name }}` and we can use control flows like `{% if variable_name == true %} some HTML {% endif %}`. The big benefit of this is that we can define `site` variables in the `_config.yml` file and use them like `{{ site.askforme.url }}`, and we can define page-specific variables in the YAML front matter at the top of each `*.html` file and use them like `{{ page.variable }}`. Take a look at the HTML files in this project to get a sense for how these things are used --- it probably sounds more complicated than it is in practice!

Similar to the HTML being augmented, the CSS is is also augmented using [SCSS](https://sass-lang.com/documentation/syntax). You can just use CSS if you want, or you can get "*sassy*" and use SCSS on top of that.
