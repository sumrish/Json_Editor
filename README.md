

# JSONIFY 

This is a project built with [Svelte](https://svelte.dev), JS, CSS and HTML. 

See [http://jsonedit.surge.sh/](http://jsonedit.surge.sh/)

## Functionality
- The app allows the user to upload a JSON file, edit it, validate it, and save it to the local workstation. One can also type up a JSON from scratch on the site and thereafter download it after validation. If the typed up JSON is wrong, the box will outline pink, and if typed correctly, it will auto format and indent the json. 
- Svelte was used because it was a fast way to build a static front end using the same/related tech stack leveraged by the potential end user of this app. Besides, a basic understanding of HTML, javascript, and CSS was all that was needed to use it. The framework compiles components into efficient JavaScript code, leading to faster loading times. Its unique approach results in a leaner codebase, reducing the amount of code processed by the browser. With minimal state management and no virtual DOM, Svelte enables faster and more reliable apps. Additionally, the compiled Svelte applications have no traces of the framework, offering a lightweight and clean final product. As a result, it is increasingly popular based on the latest [SO](https://survey.stackoverflow.co/2023/#section-admired-and-desired-web-frameworks-and-technologies) survey. 

- The code can be improved a lot, given more time. For example, the css can be separated into its own css file and referenced by the svelte code. Additionally, methods can be improved to be more SOLID.
- Two files (`config.json` and `data.json`) have been attached under `/test-files`. The former when uploaded will not work due to invalid JSON and the latter will work. 


## How the app is built 

- By using `rollup-plugin-svelte`, we have arranged for the Svelte code to be compiled. See the `scripts` section of `package.json` to find the specific commands that are run by rollup. 


## How the app is deployed on the web
- We use `surge` to deploy to the cloud. 
- See [http://jsonedit.surge.sh/](http://jsonedit.surge.sh/)
- See [Codesandbox](https://codesandbox.io/s/github/sumrish/Json_Editor)

