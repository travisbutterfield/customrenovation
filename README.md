# Custom Renovation

This is a custom sub-subtheme for Webspark 2, based on the Renovation subtheme of the Radix theme. I have imported the Sass variables from Renovation to make it easier for us to do Sass front-end development.

## Instructions for installation and use
1. If you plan on installing this module via composer (`composer install asuwatts/customrenovation:dev-main`), you will not be able to customize it for your site.
   1. However, if you would like to use it as a starting point for a custom theme, you can install it via composer and then move it out of the web/themes/composer directory and place it one level up (at web/themes/).
   2. Then you will need to remove it from your composer.json and composer.lock files: `composer remove asuwatts/customrenovation`
   3. After that, you will need to make sure that the references to the Sass variables are updated. Most likely you will need to do a find/replace changing `../../../webspark-theme-renovation` to be `../../../composer/webspark-theme-renovation` in the "customrenovation/src/sass/customrenovation.style.scss" file (which is where you should make any Sass/css edits).
   4. From this point, be aware that the theme will be unique to your site and won't receive any updates from the original source in github.

### Browsersync setup
In order to make this subtheme work with Browsersync for local front-end development, you will need to make a few changes.
1. You will need to set Drupal 9 up for local development by creating a "web/sites/default/settings.local.php" file. 
   1. The easiest way to do this is to open the "web/sites/example.settings.local.php" file and follow the directions. This will disable some of the caching in Drupal so that you won't have to rebuild the cache every time you make a change in your local environment.  
2. After setting your site up for local development, open the "customrenovation/webpack.mix.js" file and enter your site's name on the line that says `const proxy = '<sitename>.ddev.site';` (without the < > symbols). Then save the file. Please note the lack of `http://` or `https://` protocols. Including the protocol will prevent browsersync from working properly.
3. After you have followed these instructions, run `ddev ssh`. 
4. You will most likely need to open port 3000 if you want to use browsersync. To do so, you will need to create a new file in the .ddev directory at the root level of your site. The new file should be named "docker-compose.webpack.yaml". The contents of this file should be as follows:
```yaml
version: "3.6"
services:
   web:
      expose:
         - 3000
      environment:
         - HTTP_EXPOSE=${DDEV_ROUTER_HTTP_PORT}:80,${DDEV_MAILHOG_PORT}:8025,3001:3000
         - HTTPS_EXPOSE=${DDEV_ROUTER_HTTPS_PORT}:80,${DDEV_MAILHOG_HTTPS_PORT}:8025,3000:3000
```
5. You will need to restart ddev for these changes to come into effect: `ddev restart`. 
6. After ddev has successfully restarded, navigate to the "web/themes/customrenovation" subtheme folder in your terminal.
7. Run `npm install` from the within the subtheme folder.
8. After npm has finished installing, run `npm run watch`, also from the subtheme folder.
9. To utilize browsersync, don't use the <span>htt</span>ps://localhost:3000 option that is provided. Instead, navigate to [https://\<sitename>.ddev.site:3000](https://\<sitename>.ddev.site:3000). (Again, replace `<sitename>` with the short name of your site).
