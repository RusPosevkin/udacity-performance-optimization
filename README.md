## Website Performance Optimization portfolio project

Your challenge, if you wish to accept it (and we sure hope you will), is to optimize this online portfolio for speed! In particular, optimize the critical rendering path and make this page render as quickly as possible by applying the techniques you've picked up in the [Critical Rendering Path course](https://www.udacity.com/course/ud884).

## How to start
1. Clone this repository https://github.com/RusPosevkin/udacity-performance-optimization.git

2. Run a local server
  ```bash
  $> cd /path/to/your-project-folder
  $> python -m SimpleHTTPServer 8080
  ```
3. Open a browser and visit http://localhost:8080/

4. Download and install [ngrok](https://ngrok.com/) to the top-level of this project directory to make local server accessible remotely.

  ``` bash
  $> cd /path/to/your-project-folder
  $> ./ngrok http 8080
  ```

5. Copy the public URL ngrok gives you and try running it through PageSpeed Insights!

## What's done
* PageSpeed Score
  * Add media type for print.css request (download only for printing)
  * views/images/pizzeria.jpg size optimized
  * Minify js/css
  * Inline render blocking CSS: it is applied to the document immediately instead of blocking loading.
  * Disabled loading of Open Sans font (blocking rendering)
* Getting Rid of Jank (all optimizations you can find into the code with prepending "optimization:" comment)
  * Cached array length property (when we used them in the loop)
  * Cached DOM node properties (when we used them in the loop)
  * Divide relayout and repaint operations in the loop (to reduce recalculate style time)
  * Use createDocumentFragment to reduce count of DOM manipulations
  * Reduce count of generating moving pizzas to 20 (it's still enough to cover the screen)
  * Add new paint layer for every moving pizza ("will-transform")
  * Cache all moving pizza items DOM node once after initialization
  * Move DOM node style constant properties to CSS
  * Grid classes instead of inline CSS rules
