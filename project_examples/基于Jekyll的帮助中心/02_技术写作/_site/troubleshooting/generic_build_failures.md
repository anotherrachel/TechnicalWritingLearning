# Unverified email address
To trigger a build, the user who pushes a commit to the Pages repository must have a [verified email address](https://help.github.com/en/articles/verifying-your-email-address).

After you verify an email address, your GitHub Pages sites will build automatically.

# Deploy key used for push
Pushes must come from a user account with a verified email address. You won't trigger a build if you use a [deploy key](https://developer.github.com/guides/managing-deploy-keys/#deploy-keys) to push to an organization's Pages repository.

Instead, you can [set up a machine user as a member of your organization](https://developer.github.com/guides/managing-deploy-keys/#machine-users).

# Size limits
Repositories on GitHub have a soft limit of 1 GB per repository. Similarly, GitHub Pages sites also have a 1 GB soft limit.

If your Pages site exceeds that limit, you may find that your site won't build. You may also receive a polite email from us requesting that you reduce the size of your site.

# Source setting
Our build server overrides the `source` setting when it builds Pages sites. If you change this setting in your *_config.yml* file, your GitHub Pages site may not build correctly.

