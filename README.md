# cpanel-404-error-on-refresh-of-urls
how to solve react router issues after deployment in cpanel 404 error on refresh of urls

Here is code .

<IfModule mod_rewrite.c>
  RewriteEngine On
  RewriteBase /
  RewriteRule ^index\.html$ - [L]
  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteCond %{REQUEST_FILENAME} !-d
  RewriteRule . /index.html [L]
</IfModule>
