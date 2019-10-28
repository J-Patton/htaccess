# .htaccess optimization

``` <ifModule mod_gzip.c>
<ifModule mod_gzip.c>
mod_gzip_on Yes
mod_gzip_dechunk Yes
mod_gzip_item_include file .(html?|txt|css|js|php|pl)$
mod_gzip_item_include handler ^cgi-script$
mod_gzip_item_include mime ^text/.*
mod_gzip_item_include mime ^application/x-javascript.*
mod_gzip_item_exclude mime ^image/.*
mod_gzip_item_exclude rspheader ^Content-Encoding:.*gzip.*
</ifModule>

AddOutputFilterByType DEFLATE text/plain
AddOutputFilterByType DEFLATE text/html
AddOutputFilterByType DEFLATE text/xml
AddOutputFilterByType DEFLATE text/css
AddOutputFilterByType DEFLATE application/xml
AddOutputFilterByType DEFLATE application/xhtml+xml
AddOutputFilterByType DEFLATE application/rss+xml
AddOutputFilterByType DEFLATE application/javascript
AddOutputFilterByType DEFLATE application/x-javascript

# BEGIN Expire headers
<ifModule mod_expires.c>
        ExpiresActive On
        ExpiresDefault "access plus 2 days"
        ExpiresByType image/x-icon "access plus 2592000 seconds"
        ExpiresByType image/jpeg "access plus 2592000 seconds"
        ExpiresByType image/png "access plus 2592000 seconds"
        ExpiresByType image/gif "access plus 2592000 seconds"
        ExpiresByType application/x-shockwave-flash "access plus 2592000 seconds"
        ExpiresByType text/css "access plus 604800 seconds"
        ExpiresByType text/javascript "access plus 216000 seconds"
        ExpiresByType application/javascript "access plus 216000 seconds"
        ExpiresByType application/x-javascript "access plus 216000 seconds"
        ExpiresByType text/html "access plus 600 seconds"
        ExpiresByType application/xhtml+xml "access plus 600 seconds"
</ifModule>
# END Expire headers


# BEGIN Caching
<ifModule mod_headers.c>
  <filesMatch "\\.(ico|pdf|flv|jpg|jpeg|png|gif|swf|svg)$">
    Header set Cache-Control "max-age=2592000, public"
  </filesMatch>
  <filesMatch "\\.(css|js)$">
    Header set Cache-Control "max-age=604800, public"
  </filesMatch>
  <filesMatch "\\.(xml|txt)$">
    Header set Cache-Control "max-age=216000, public, must-revalidate"
  </filesMatch>
  <filesMatch "\\.(html|htm|php)$">
    Header set Cache-Control "max-age=3600, public, must-revalidate"
  </filesMatch>
</ifModule>
# END Caching```
