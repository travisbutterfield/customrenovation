# Custom Renovation

This is a custom sub-subtheme for Webspark 2, based on the Renovation subtheme of the Radix theme. I have imported the Sass variables from Renovation to make it easier for us to do Sass front-end development.

##Instructions for use
1. In order to make this subtheme work with Browsersync for local front-end development, you will need to make one change. Open the webpack.mix.js file and enter your site's name on the line that says "const proxy = 'http://<sitename>.ddev.site';". Then save the file. 
2. After you have followed these instructions, navigate to the subtheme folder in your terminal and run "npm install".
3. After npm has finished installing, run "npm run watch".
4. Please note that if you are using something like ddev or lando, you will need to prepend these commands or ssh into your container before running them.
