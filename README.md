This jQuery plugin creates beautiful simple rating systems with minimal html and JavaScript.
It is highly customizable if needed and integrates with font-awesome icons
It requires jQuery any version 1.8 onwards

Include the plugin

`<script src="jQuery-gRating.min.js"></script>`

Add a html element for each rating needed

`<div class="rating" value="3"></div>`

Initialize the plugin for elements on the page you want to be gRated

    <script>
        $(".rating").grating();
    </script>
	
That's it!

The plugin supports chaining so you can use normal jQuery functions after initializing gRating

You can get the current value, enable or disable, initialize many ratings on a page in one call

Ratings are character based so you can use any character, html element or Font Awesome icon definitions

Methods
* enable(true|false) - Set the collection of ratings to enabled or disabled

`$(".rating").grating().enable(true);`

* val(index) - Get the collection of ratings current value or a single value, pass in an optional index to get an    individual value from a collection

`$(".rating").grating().val();`

Properties with their default values

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
      callback: function(owner, value)
      {
        //Owner is the rating div from our earlier example it doesn't have an id value but we could easily add one to identify the purpose of the rating
        console.log("Callback from "+owner.attr("id")+" with value "+value);
      },
      //Font awesome icon code is all that's needed to have them injected
      character: "fa-ambulance",
      //Change the rating css color to a more appropriate example for out page design
      ratingCss: {color: "#5D6D7E"}
    });
