# Custom Renovation

This is a custom sub-subtheme for Webspark 2, based on the Renovation subtheme of the Radix theme. I have imported the Sass variables from Renovation to make it easier for us to do Sass front-end development.

##Instructions for use
1. If you plan on installing this module via composer, you will not be able to customize it for your site. However, if you would like to use it as a starting point for a custom theme, you can move it out of the web/themes/composer directory and place it one level up (at web/themes/). 
   1. Then you will need to remove it from your composer.json and composer.lock files. `composer remove asuwatts/customrenovation` 
   2. After that, you will need to make sure that the references to the Sass variables are updated. Most likely you will need to do a find/replace changing "../../../webspark-theme-renovation" to be "../../../composer/webspark-theme-renovation."
   3. From this point,  be aware that the theme will be unique to your site and won't receive any updates from the original source in github/composer.
2. In order to make this subtheme work with Browsersync for local front-end development, you will need to make one change. Open the webpack.mix.js file and enter your site's name on the line that says "const proxy = '\<sitename>.ddev.site';". Then save the file. (Please note the lack of http:// or https://)
3. After you have followed these instructions, navigate to the subtheme folder in your terminal.
4. Run `npm install` from the subtheme folder.
5. After npm has finished installing, run `npm run watch` also from the subtheme folder.
6. Please note that if you are using something like ddev or lando, you will need to prepend these commands with "ddev" or "lando," or you can ssh into your container before running them.
