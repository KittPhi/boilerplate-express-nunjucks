# boilerplate-express-html

> Referenced [Original Github](https://github.com/KittPhi/nunjucks-examples/tree/bd8827bcc951d3bb4622c588e25d43bfd85a95b2/6_exp_gen_nun_templ_h%26f)
> Referenced [Nunjucks and Express App Tutorial](https://regbrain.com/article/nunjucks-express-app)

## History

```js
npx express-generator myapp --no-view
// or
npx express-generator . --no-view
// then
npm i express dotenv nunjucks

// mkdir
mkdir views && touch views/layout.njk && touch views/index.njk

// We are going to specify nunjucks as the view engine
// So get rid of the placeholder `index.html` in /public.
mv public/index.html old-index.html

// At `app.js` configute Nunjucks with 'views' as templates directory
let nunjucks = require("nunjucks");

nunjucks.configure("views", {
  autoescape: true,
  express: app,
});

// Render `index.njk` when someone visits home; edit `/routes/index.js`
let express = require("express");
let router = express.Router();

router.get("/", async function (req, res, next) {
  let data = {
    title: "Nunjucks example",
    layout: "layout.njk",
    message: "Hello world!",
  };

  res.render("index.njk", data);
});

module.exports = router;

// Start app
yarn start

// open in browser
http://localhost:3000/
```

## Takeaway:

> We are feeding `layout.njk` template into `index.njk`

> Configured inside `routes/index.js` we are passing `data = {layout: "layout.njk"}` into `res.render("index.njk", data);`
