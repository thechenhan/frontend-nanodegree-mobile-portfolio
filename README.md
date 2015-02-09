####Website Performance Optimization Final Project
##What is this
This is the course project for Google & Udacity course, "Website Performance Optimization". For more information
you can click [here] (https://www.udacity.com/course/ud884-nd); The project has two goals. 1st, perform optimizations to achieve a PageSpeed score above 90 on index.html. 2nd, optimized the pizza.index page, to increase the animation FPS at 60fps, reduce the resize pizza time less than 5ms.
##The result
The final results are shown as these two following figures. The mobile score is 95/100 and desktop score is 97/100. The FPS is very good, and the time to resize is ~1ms (reduced from 95ms). 
![opt1](https://github.com/thechenhan/frontend-nanodegree-mobile-portfolio/blob/master/img/optimization-result-1.png?raw=true "index.html optimization result"); ![opt2](https://github.com/thechenhan/frontend-nanodegree-mobile-portfolio/blob/master/img/optimization-result-2.png?raw=true "pizza.html optimization result"); 
##Check it out
Please click [here] (http://thechenhan.github.io/frontend-nanodegree-mobile-portfolio/), also you can go to find the detailed information in the files. I made detailed comments there.
##The optimizations outline
Mainly modified files: index.html, /views/js/main.js, /views/css/style.css
#Index.html
* I optimized the google font calling. Change the google font css inline to eliminate the CSS rending block.
* I put some header style setting inline, to eliminate external render-blocking JavaScript and CSS in above-the-fold content.
* Use CSS media queries for responsiveness and eliminate rendering block.
* Compress the pictures size, for pizza.jpg.
* Put async tag to google analytics and perfmatters to remove this js out of CRP.
#Pizza.html
* I optimized changePizzaSizes() function. I moved all of the variables out of the loop, because these values are constant, we only need to calculate once. Reduced the "change size" time from ~95ms to less than 1ms.
* I optimized updatePositions() function. Method 1, pre-save the .mover class, to reduce the selection time.Method 2, rather than update the "left" property which require layout, paint and composite time. I used transform method which only takes composite time.
* I used Hardware-Accelerated CSS, backface-visibility and perspective, for .mover and .randomPizzaContrainer classes.
* I optimized the 'scroll' calling function. Before optimization, the updatePosition function will be called as soon as the user scrolls the window, however it does not give the best performance. I use the requestAnimationFrame() function to get the best performance of the browers. In other to avoid multi-calling of the requestAnimationFrame when the users consecutivly scroll the window, I set up a gobal flag varible ticking. If ticking = true, means the updating is running, the following requests will be blocked. Only if the ticking = false (default), the requestAnimationFrame() will be called.
* Reduced the pizza number from 200 to a suitable amount. It depends on the windoe sizes. 

##Reference
Thank you all!
* https://developers.google.com/speed/pagespeed/insights/
* https://developers.google.com/web/fundamentals/performance/critical-rendering-path/
* http://www.html5rocks.com/en/tutorials/speed/high-performance-animations/
* http://blog.teamtreehouse.com/increase-your-sites-performance-with-hardware-accelerated-css
* http://http://jankfree.org/
* https://www.youtube.com/watch?v=YyQYhhy1dZI
* http://www.html5rocks.com/en/tutorials/speed/animations/
* https://github.com/bahalps/frontend-nanodegree-mobile-portfolio
* https://github.com/bahalps/frontend-nanodegree-mobile-portfolio
