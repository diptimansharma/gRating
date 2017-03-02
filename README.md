This jQuery plugin creates beautiful simple rating systems with minimal html and JavaScript.
It is highly customizable if needed and integrates with font-awesome icons
It requires jQuery any version 1.6+ for the use of the prop function

## Using gRating

Download the latest release from the [Github releases page](https://github.com/duindain/gRating/releases)

Include the plugin

`<script src="jQuery-gRating.min.js"></script>`

Add a html element for each rating needed

`<div class="rating" value="3"></div>`

Initialize the plugin for elements on the page you want to be gRated

    <script>
        $(".rating").grating();
    </script>
	
That's it!

## Getting Help

There is an examples page at [http://lazinator.com/grating/](http://lazinator.com/grating/) which demonstrates the common use cases for gRating with the code shown to reproduce each feature.

Visit the Blog about gRating at [http://lazinator.com/Articles/Duindain-gRating.php](http://lazinator.com/Articles/Duindain-gRating.php) and submit a comment.

If you think you've found a bug in gRating, please write a reproducible test case and file a [Github](https://github.com/duindain/gRating/issues) issue.

## Changelog

To see a changelog with all gRating releases, check out the [Github releases page](https://github.com/duindain/gRating/releases).

## More details

The plugin supports chaining so you can use the result of the initialization operation in other jQuery calls

You can get the current value, enable or disable, initialize many ratings on a page in one call

Ratings are character based so you can use any character, alternatively you can use html element's, Font Awesome icon definitions or spritesheets and images

You can provide data overrides in html to customize the rating, these values override plugin settings when present i.e.

`<div class="rating" value="1" data-character="fa-ambulance" data-clickLimit="2" data-max="7"></div>`

This will create a rating with the following settings
* An initial selected value of 1 
* Using the Font-Awesome Ambulance icon
* A click limit of 2 times
* 7 element's in the rating

### Methods
* enable(true|false) - Set the collection of ratings to enabled or disabled

`$(".rating").grating().enable(true);`

* val(index) - Get the collection of ratings current value or a single value, pass in an optional index to get an    individual value from a collection

`$(".rating").grating().val();`

* character(function() {}) - Override the character generation to provide your own dynamic set of characters

`$(".rating").grating().character(function(index) { return index;});`

### Plugin properties

    $.fn.grating = function(options) {
        /* Default plugin options */
        $.fn.grating.defaultOptions = {
          enabled: true,//Initial enabled or disabled state of the rating
          allowDeselect: true,//Indicates whether to allow select the same rating value twice to toggle off the rating
          character: "&#9733;",//Default character to use i.e. ASCII Star, can be font-awesome fa codes i.e. fa-ambulance
          elementType: "span",//Allows switching the span type to another html element if needed
          elementCount: 5,//How many rating objects to display
          clickLimit: 0,//Whether to limit the number of clicks or not, a value of 0 enables no limit
          defaultValue: 0,//Initial rating value
          callback: null,//Placeholder for callback function called onclick events for when a rating is changed
          ratingCss: {//Normal display settings for stars
            fontSize: "50px",
            color: "#fff",//For dark pages
            opacity: ".5",
            cursor: "pointer",
            padding: "0 10px",
            transition: "all 150ms",
            display: "inline-block",
            transform: "rotateX(45deg)",
            transformOrigin: "center bottom",
            textShadow: "none"
          },
          ratingHoverCss: {//Hover settings for stars
            color: "#ff0",
            opacity: "1",
            transform: "rotateX(0deg)",
            textShadow: "0 0 30px #ffc"
          }
    };

Properties can be overridden when initilizing the gRating plugin

    $(".rating").grating({
      //Font awesome icon code is all that's needed to have them injected
      character: "fa-ambulance",
      //Change the rating css color to a more appropriate example for our page design
      ratingCss: {color: "#5D6D7E"}
    });

You can add a callback function to the plugin by passing it in on initialization, this will get called when a click event is detected on the rating. It passes back the rating object and the new value for the rating.

    $(".rating").grating({
      callback: function(owner, value)
      {
        //Owner is the rating div from our earlier example it doesn't have an id value but we could easily add one to    identify the purpose of the rating
        console.log("Callback from "+owner.attr("id")+" with value "+value);
      }
    });
