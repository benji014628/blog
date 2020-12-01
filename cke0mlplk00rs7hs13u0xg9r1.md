## TailwindCSS Tutorial w/ Official TailwindCSS-IntelliSense Extension & Typography Plugin

You're ready to start on a fresh new project and to use the nifty [utility-first CSS framework Tailwind](https://tailwindcss.com/) with [IntelliSense VS Code extension](https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss/) and the latest [Typography plugin](https://tailwindcss.com/docs/typography-plugin/).

# Installation

## 1. Create project & initialize npm

Choose a folder or create a new one with your project name. The quickest approach to do this is through the terminal by simply typing:

```
mkdir tailwind-beginner-project
``` 

(you can change the name to whatever you want)

Next, we're going to initialize npm, which will give us a `package.json` file and the ability to install TailwindCSS:

```
cd tailwind-beginner-project
npm init -y
``` 

## 2. Install Tailwind via npm

Now to install TailwindCSS, simply run:

```
npm i tailwindcss
``` 

You can open your package.json and you should see tailwindcss under your dependencies:

```
{
  "name": "tailwind-beginner-project",
  "version": "1.0.0",
  "description": "",
  "main": "",
  "dependencies": {
    "tailwindcss": "^1.7.0"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}

``` 

## 3. Add Tailwind to your CSS

Next, we need to set up a CSS file for our project. Create a new CSS file in your project and name it whatever you want. Mine will be main.css. Then, in that file, include these three Tailwind directives:

```
@tailwind base;
@tailwind components;
@tailwind utilities;
```
Tailwind will swap these directives out at build time with all of its generated CSS.

If you are eager to drop over to your HTML and begin coding, we only need to do two small steps. First, go over to your package.json file and under the ending brace of "dependencies" add this:

```
"scripts": {
    "build": "tailwindcss build main.css -o tailwind.css"
  }
```
(you can name the output file anything you want)

And run this script in your terminal:

```
npm run build
```
Congrats! You've now installed TailwindCSS and have it running. Now you might be wondering how to customize these new utilities well in these next steps are for you.

## 4 Create your Tailwind config file (optional)

You can generate a config file for your project by typing: 

```
npx tailwindcss init
```
Hopefully, you see a new `tailwind.config.js` fill pop up in your project and can now start working on your project, unless you want a handy extension, into typography or both! 

## 5 Final Step

Go over to your activity panel, click on the symbol with those four boxes, and search `Tailwind CSS IntelliSense` and press install. Next to install the typography plugin open up the terminal and type:

```
npm install @tailwindcss/typography
```

Then add the plugin to your tailwind.config.js file:

```
module.exports = {
  purge: [],
  theme: {
    extend: {},
  },
  variants: {},
  plugins: [require('@tailwindcss/typography')],
}
```
You've finally set up TailwindCSS with IntelliSense and the typography plugin. Follow these steps for all your future Tailwind projects. 

Thank you for reading my blog and enjoy coding with your new CSS framework! Feel free to subscribe to my email newsletter and connect on Twitter.




