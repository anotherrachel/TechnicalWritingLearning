# "Page build failed: Missing docs folder"
If you have the master branch /docs folder source setting enabled and your /docs folder with your site's source files was removed from the root of your repository on the master branch, your GitHub Pages site will not build.

## Resolving the build error
If your `/docs` folder was accidently moved, you can try moving the `/docs` folder back to the root of your repository on the `master` branch.

If your `/docs` folder was deleted, you must either:

- use Git to revert or undo the deletion of your`/docs` folder with your site's source files
- recreate a `/docs` folder in the root of your repository on the `master` branch and add or recreate your site's source files in this folder
- change the source settings to `gh-pages` or the `master` branch and add or recreate your site's source files on the `gh-pages` or `master` branch

# "Page build failed: Markdown errors"
If your GitHub Pages code contains Markdown errors, your GitHub Pages site will not build.

## Troubleshooting Markdown errors

If you are not using kramdown as your Markdown processor, then you must update your Markdown processor to kramdown. GitHub Pages only supports kramdown.

Make sure the file in question uses valid Markdown syntax. 

Once you've fixed any Markdown errors, you will need to commit your changes and push to your GitHub Pages repository again to trigger another build on the server.

# "Page build failed: Config file error"
If the *_config.yml* file in your GitHub Pages repository has syntax errors, your GitHub Pages site will not build.

## Troubleshooting *_config.yml* syntax errors

Check your *_config.yml* file at the line referenced in the build failure email. Ensure that:

- You are using spaces instead of tabs in the file.

- You have included a space after the ":" for each key/value pair.

  Correct example: `timezone: Africa/Nairobi`

  Build fail example: `timezone:Africa/Nairobi`.

- You are only using UTF-8 characters.

- You quote any special characters.

  Correct example: `title: "my awesome site: an adventure in parse errors"`

  Build fail example: `title: my awesome site: an adventure in parse errors`

Use a YAML linter, such as <http://codebeautify.org/yaml-validator>, to validate your YAML code. If you run into parse errors with your *_config.yml* file, try copying and pasting the contents of the file into such a tool for more details.

Once you've fixed any syntax errors in your *_config.yml* file, you will need to commit your changes and push to your GitHub Pages repository again to trigger another build on our servers.

# "Page build failed: File does not exist in includes directory"
If your GitHub Pages code references a file that doesn't exist in your _includes directory, your GitHub Pages site will not build.

## Troubleshooting a nonexistent file error

1. Use your favorite text editor to open the file mentioned in the build failure email.
2. Search for the `include` tag to see where you've referenced other files. For example: `{% include example_header.html %}`.
3. If you've referenced any files that aren't in the *_includes* directory of your GitHub Pages repository, you will need to copy or move them into the *_includes* directory. If the files don't exist at all, you will need to create them.
4. Commit the changes and push them to your GitHub Pages repository to trigger another build on the server.

# "Page build failed: File is not properly UTF-8 encoded"
If your GitHub Pages repository contains a file that is not properly UTF-8 encoded, your GitHub Pages site will not build.

## Troubleshooting UTF-8 encoding errors

Computers expect text to appear as Latin characters. Encoding errors occur when you use non-Latin characters, like `日本語`, without telling the computer to expect these symbols.

To force UTF-8 encoding, add the following line to your *_config.yml* file:`encoding: UTF-8`

After you make this change, you will need to commit your changes and push to your Pages repository on GitHub to trigger another build on the server.

# "Page build failed: Invalid post date"
If your GitHub Pages repository contains a post with an invalid date, your GitHub Pages site will not build.

## Troubleshooting post date errors

- Make sure you're using proper date formatting for filenames with dates and any date values in the YAML front matter of your files. Dates must be formatted as YYYY-MM-DD HH:MM:SS for UTC, and must be actual calendar dates.
- If you specify a date format in your *_config.yml* file, make sure you format it correctly. To specify a time zone with an offset from UTC, use the format YYYY-MM-DD HH:MM:SS +/-TTTT. For example: `2014-04-18 11:30:00 +0800`.

Once you've fixed all post date errors, you will need to commit your changes and push to your GitHub Pages repository again to trigger another build on the server.

# "Page build failed: Invalid YAML in data file"
If one or more files in the _data folder of your GitHub Pages site contains invalid YAML, your GitHub Pages site will not build.

## Troubleshooting YAML parsing errors

Check the YAML files in your `_data` folder for the following:

- Check the indentation in your YAML file and remove any tab characters, as these may not conform to the [suggested spacing for YAML files](http://www.yaml.org/spec/1.2/spec.html#id2777534).

- Ensure that you have a space between a key's value and its preceding colon.

  Correct example: `key: value`

  Build fail example: `key:value`

- Check your entries for multi-line values. Including a `|` will create newlines for each line in the value while including `>` will ignore newlines and leave all content on a single line.

- Ensure that you're using appropriate quotations. You may need to quote URLs as well as variables or strings that begin with or contain YAML special characters following a colon.


Once you've fixed any YAML errors, you will need to commit your changes and push to your GitHub Pages repository again to trigger another build on the server.

## 

