# Custom Renovation

This is a custom sub-subtheme for Webspark 2, based on the Renovation subtheme of the Radix theme. I have imported the Sass variables from Renovation to make it easier for us to do Sass front-end development.

##Instructions for use
1. In order to make this subtheme work with Browsersync for local front-end development, you will need to make one change. Open the webpack.mix.js file and enter your site's name on the line that says "const proxy = 'http://<sitename>.ddev.site';". Then save the file. 
2. After you have followed these instructions, navigate to the subtheme folder in your terminal and run "npm install".
3. After npm has finished installing, run "npm run watch".
4. Please note that if you are using something like ddev or lando, you will need to prepend these commands or ssh into your container before running them.
5. If you plan on installing this module via composer, you will not be able to customize it. However, if you would like to customize it, you can move it out of the web/themes/composer directory and place it one level up (at web/themes/). Then you will need to remove it from your composer.json and composer.lock files. From this point, it should be unique to your site and won't receive any updates from the original source in github/composer.
