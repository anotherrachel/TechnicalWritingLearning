Common errors and the steps needed to troubleshoot them are listed here. If you’re using a PC, rename your shell files with a .bat extension.

# “page 0” cross references in the PDF

If you see “page 0” cross-references in the PDF, the URL doesn’t exist. Check to make sure you actually included this page in the build.

If it’s not a page but rather a file, you need to add a `noCrossRef` class to the file so that your print stylesheet excludes the counter from it. Add `class="noCrossRef"` as an attribute to the link. In the *css/printstyles.css* file, there is a style that should remove the counter from anchor elements with this class.

# The PDF is blank

Check the prince-list.txt file in the output to see if it contains links. If not, you have something wrong with the logic in the *prince-list.txt* file. Check the *conditions.html* file in your *_includes* to see if the audience specified in your configuration file aligns with the buildAudience in the *conditions.html* file

# Sidebar isn't appearing

If you build your site but the sidebar doesn’t appear, check the following:

Look in your PDF config file and make sure you have a sidebar property, such as this:

```terminal
pdf_sidebar: product2_sidebar
```

Make sure each TOC item has an output property that specifies web or pdf.


# Sidebar isn’t collapsed

If the sidebar levels aren’t collapsed, usually your JavaScript is broken somewhere. Open the JavaScript Console and look to see where the problem is. If one script breaks, then other scripts will break too, so troubleshooting it is a little tricky.

# Search isn’t working

If the search isn’t working, check the JSON validity in the *search.json* file in your output folder. Usually something is invalid. Identify the problematic line, fix the file, or put `search: exclude` in the frontmatter of the file to exclude it from search.