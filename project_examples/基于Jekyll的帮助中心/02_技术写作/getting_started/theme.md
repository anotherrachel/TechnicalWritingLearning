<h1 id="title1">Build the Theme</h1>

Follow these instructions to build the theme.

<h2 id="title2">1. Download the theme</h2>

First, download or clone the theme from the [Github repo](https://github.com/tomjoht/documentation-theme-jekyll). Most likely you won’t be pulling in updates once you start customizing the theme, so downloading the theme (instead of cloning it) probably makes the most sense. In Github, click the **Clone or download** button, and then click **Download ZIP**.

<h2 id="title3"> 2. Install Jekyll</h2>

If you’ve never installed or run a Jekyll site locally on your computer, follow these instructions to install Jekyll:

- [Install Jekyll on Mac](https://idratherbewriting.com/documentation-theme-jekyll/mydoc_install_jekyll_on_mac.html)
- [Install Jekyll on Windows](https://idratherbewriting.com/documentation-theme-jekyll/mydoc_install_jekyll_on_windows.html)

<h2 id="title4"> 3. Install Bundler</h2>

In case you haven’t installed Bundler, install it:

```
gem install bundler
```

You’ll want [Bundler](http://bundler.io/) to make sure all the Ruby gems needed work well with your project. Bundler sorts out dependencies and installs missing gems or matches up gems with the right versions based on gem dependencies.

<h2 id="title5">4. Option 1: Build the Theme (without the github-pages gem)</h2>

Use this option if you’re not planning to publish your Jekyll site using [Github Pages](https://pages.github.com/).

Bundler’s *Gemfile* specifies how project dependencies are managed. Although this project includes a *Gemfile*, this theme doesn’t have any dependencies beyond core Jekyll. The *Gemfile* is used to list gems needed for publishing on Github Pages. **If you’re not planning to have Github Pages build your Jekyll project, delete these two files from the theme’s root directory:**

- *Gemfile*
- *Gemfile.lock*

If you’ve never run Jekyll on your computer (you can check with `jekyll --version`), you may need to install the jekyll gem:

```
gem install jekyll
```

Now run jekyll serve (first change directories (`cd`) to where you downloaded the project):

```
jekyll serve
```

<h2 id="title6">4. Option 2: Build the Theme (with the github-pages gem)</h2>

If you *are* in fact publishing on Github Pages, leave the *Gemfile* and *Gemfile.lock* files in the theme.The *Gemfile* tells Jekyll to use the github-pages gem. **However, note that you cannot use the normal jekyll serve command with this gem due to dependency conflicts between the latest version of Jekyll and Github Pages** (which are noted [briefly here](https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/)).

You need Bundler to resolve these dependency conflicts. Use Bundler to install all the needed Ruby gems:

```
bundle update
```

Then *always* use this command to build Jekyll:

```
bundle exec jekyll serve
```

If you want to shorten this long command, you can put this code in a file such as jekyll.sh (on a Mac) and then simply type `. jekyll.sh` to build Jekyll.
