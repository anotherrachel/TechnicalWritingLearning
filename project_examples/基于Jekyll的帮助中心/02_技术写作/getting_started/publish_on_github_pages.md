<h1 id="title1">Setting up your GitHub Pages site locally with Jekyll</h1>

> GitHub Pages is available in public repositories with GitHub Free, and in public and private repositories with GitHub Pro, GitHub Team, GitHub Enterprise Cloud, and GitHub Enterprise Server. For more information, see "[GitHub's products](https://help.github.com/articles/github-s-products)."

You can set up a local version of your Jekyll GitHub Pages site to test changes to your site locally. We highly recommend installing Jekyll to preview your site and help troubleshoot failed Jekyll builds.

<h2 id="title2">Requirements</h2>

We recommend using [Bundler](http://bundler.io/) to install and run Jekyll. Bundler manages Ruby gem dependencies, reduces Jekyll build errors, and prevents environment-related bugs. To install Bundler, you must install [Ruby](https://www.ruby-lang.org/).

1. Open the terminal.

2. Check whether you have Ruby 2.1.0 or higher installed:

   ```shell
   $ ruby --version
   > ruby 2.X.X
   ```

3. If you don't have Ruby installed, [install Ruby 2.1.0 or higher](https://www.ruby-lang.org/en/downloads/).

4. Install Bundler:

   ```shell
   $ gem install bundler
   # Installs the Bundler gem
   ```

5. If you already have a local repository for your Jekyll site, skip to **Step 2**.

<h2 id="title3">Step 1: Create a local repository for your Jekyll site</h2>

1. If you haven't already downloaded Git, install it. For more information, see "[Set up Git](https://help.github.com/en/articles/set-up-git/)."

2. Open the terminal.

3. On your local computer, initialize a new Git repository for your Jekyll site:

   ```shell
   $ git init JEKYLL-SITE-REPOSITORY-NAME
   > Initialized empty Git repository in /Users/octocat/my-site/.git/
   # Creates a new file directory on your local computer, initialized as a Git repository
   ```

4. Change directories to the new repository you created:

   ```shell
   $ cd JEKYLL-SITE-REPOSITORY-NAME
   # Changes the working directory
   ```

5. If your new local repository is for a [Project pages site](https://help.github.com/en/articles/user-organization-and-project-pages/), create a new `gh-pages` branch:

   **Note:** You can skip this step if you would rather use the `master` branch for your Project Page. If you haven't checked out any branches, once you make a commit in your local repository, your change will appear on the `master` branch by default.

   ```shell
   $ git checkout -b gh-pages
   > Switched to a new branch 'gh-pages'
   # Creates a new branch called 'gh-pages', and checks it out
   ```

   > **Tip:** To learn more about creating a User, Organization or Project Page and which branch to use, see "[User, Organization, and Project Pages](https://help.github.com/en/articles/user-organization-and-project-pages)." To learn more about how to build your site's source files from a `/docs` folder on the `master` branch, see "[Configuring a publishing source for GitHub Pages](https://help.github.com/en/articles/configuring-a-publishing-source-for-github-pages/#publishing-your-github-pages-site-from-a-docs-folder-on-your-master-branch)."

<h2 id="title4">Step 2: Install Jekyll using Bundler</h2>

To track your site's dependencies, Ruby will use the contents of your *Gemfile* to build your Jekyll site.

1. Check to see if you have a *Gemfile* in your local Jekyll site repository:

   ```shell
   $ ls
   > Gemfile
   ```

   If you have a *Gemfile*, skip to **step 4**. If you don't have a *Gemfile*, skip to **step 2**.

2. If you don't have a *Gemfile*, open your favorite text editor, such as [Atom](https://atom.io/), and add these lines to a new file:

   ```shell
   source 'https://rubygems.org'
   gem 'github-pages', group: :jekyll_plugins
   ```

3. Name the file `Gemfile` and save it to the [root directory](https://en.wikipedia.org/wiki/Root_directory) of your local Jekyll site repository. Skip to step 5 to install Jekyll.

4. If you already have a *Gemfile*, open your favorite text editor, such as [Atom](https://atom.io/), and add these lines to your *Gemfile*:

   ```shell
   source 'https://rubygems.org'
   gem 'github-pages', group: :jekyll_plugins
   ```

5. Install Jekyll and other [dependencies](https://pages.github.com/versions/) from the GitHub Pages gem:

   ```shell
   $ bundle install
   > Fetching gem metadata from https://rubygems.org/............
   > Fetching version metadata from https://rubygems.org/...
   > Fetching dependency metadata from https://rubygems.org/..
   > Resolving dependencies...
   ```

<h2 id="title5">Step 3 (optional): Generate Jekyll site files</h2>

To build your Jekyll site locally, preview your site changes, and troubleshoot build errors, you must have Jekyll site files on your local computer. You may already have Jekyll site files on your local computer if you cloned a Jekyll site repository. If you don't have a Jekyll site downloaded, you can generate Jekyll site files for a basic Jekyll template site in your local repository.

If you want to use an existing Jekyll site repository on GitHub as the starting template for your Jekyll site, fork and clone the Jekyll site repository on GitHub to your local computer. For more information, see "[Fork a repo](https://help.github.com/en/articles/fork-a-repo/)."

> **Note:** As of Jekyll 3.2, the default Jekyll site contains a *Gemfile* that locks Jekyll to the Gem version you build it with. To instead lock it to the version used by GitHub Pages, you'll uncomment the `gem "github-pages", group: :jekyll_plugins` line in the steps below.

1. If you don't already have a Jekyll site on your local computer, create a Jekyll template site in a new directory:

   ```shell
   $ bundle exec jekyll _3.3.0_ new NEW-JEKYLL-SITE-REPOSITORY-NAME
   > New jekyll site installed in /Users/octocat/NEW-JEKYLL-SITE-REPOSITORY-NAME.
   ```

2. Navigate into your new site directory:

   ```shell
   $ cd NEW-JEKYLL-SITE-REPOSITORY-NAME
   ```

3. Edit your *Gemfile* and remove the following line:

   ```shell
   $ "jekyll", "3.3.0"
   ```

4. In the *Gemfile*, delete the `#` at the beginning of this line:

   ```shell
   $ gem "github-pages", group: :jekyll_plugins
   ```

5. Initialize your site directory as a Git repository.

   ```shell
   $ git init
   > Initialized empty Git repository in /Users/octocat/name-of-your-directory
   ```

6. [Connect your remote repository](https://help.github.com/en/articles/adding-a-remote/) on GitHub to your local repository for your GitHub Pages site.

   ```shell
   $ git remote add origin https://github.com/username-or-organization-name/your-remote-repository-name
   ```

7. To edit the Jekyll template site, open your new Jekyll site files in a text editor. Make your changes and save them in the text editor. You can preview these changes locally on your computer without committing your changes using Git by [running a Jekyll command to build your site](https://help.github.com/en/articles/setting-up-your-github-pages-site-locally-with-jekyll/#step-4-build-your-local-jekyll-site).

8. Add or stage your changes.

   ```shell
   $ git add .
   ```

9. Commit your changes with a comment.

   ```shell
   $ git commit -m "updated site"
   ```

10. To publish your changes on your GitHub Pages site, [push your changes](https://help.github.com/en/articles/pushing-to-a-remote/) to your remote repository on GitHub.

    ```shell
    $ git push -u origin master
    ```

For more information on using this Git workflow, see "[Good Resources for Learning Git and GitHub](https://help.github.com/en/articles/git-and-github-learning-resources/)" or see this [Git cheat sheet](https://help.github.com/en/articles/git-cheatsheet).

<h2 id="title6">Step 4: Build your local Jekyll site</h2>

1. Navigate into the [root directory](https://en.wikipedia.org/wiki/Root_directory) of your local Jekyll site repository.

2. Run your Jekyll site locally:

   ```shell
   $ bundle exec jekyll serve
   > Configuration file: /Users/octocat/my-site/_config.yml
   >            Source: /Users/octocat/my-site
   >       Destination: /Users/octocat/my-site/_site
   > Incremental build: disabled. Enable with --incremental
   >      Generating...
   >                    done in 0.309 seconds.
   > Auto-regeneration: enabled for '/Users/octocat/my-site'
   > Configuration file: /Users/octocat/my-site/_config.yml
   >    Server address: http://127.0.0.1:4000/
   >  Server running... press ctrl-c to stop.
   ```

3. Preview your local Jekyll site in your web browser at `http://localhost:4000`.

<h2 id="title7">Keeping your site up to date with the GitHub Pages gem</h2>

Jekyll is an [active open source project](https://github.com/jekyll/jekyll) and is updated frequently. As the GitHub Pages server is updated, the software on your computer may become out of date, resulting in your site appearing different locally from how it looks when published on GitHub.

1. Open the terminal.
2. Run this update command:
   - If you followed our setup recommendations and installed [Bundler](http://bundler.io/), run `bundle update github-pages` or simply `bundle update` and all your gems will update to the latest versions.
   - If you don't have Bundler installed, run `gem update github-pages`

<h2 id="title8">Next steps: Configuring Jekyll</h2>

To configure your pages site further, see "[Configuring Jekyll](https://help.github.com/en/articles/configuring-jekyll)." To set up a project pages site, see [Jekyll's official documentation on project pages URLs](http://jekyllrb.com/docs/github-pages/#project-page-url-structure).

<h2 id="title9">Further Reading</h2>

- "[Troubleshooting GitHub Pages Builds](https://help.github.com/en/articles/troubleshooting-github-pages-builds)"
- "[Using Jekyll as a static site generator with GitHub Pages](https://help.github.com/en/articles/using-jekyll-as-a-static-site-generator-with-github-pages/)"
- [Jekyll's official GitHub Pages documentation](http://jekyllrb.com/docs/github-pages/)
- [Jekyll commands](http://jekyllrb.com/docs/usage/)