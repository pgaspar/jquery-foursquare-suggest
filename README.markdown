# jQuery Foursquare Suggest Completion Plugin

A simple way to get Foursquare Venues Suggestion Completion into your site's html input fields. Type something in the input field (like "ham", "hambur", or "hamburger") and get a list of matching Foursquare Venues (in this case, Minivenues). For more information on Foursquare Suggest Completion, go [here](https://developer.foursquare.com/docs/venues/suggestcompletion "Foursquare Suggest Completion").

![alt text](http://f.cl.ly/items/3c0n3r3z0t3y3O1l3u1R/Screen%20Shot%202014-01-18%20at%2017.51.29.png "Hamburger Search")


The idea is to create something that is simple and lightweight, with no styling, so you can style it yourself (instead of figuring out how somebody else styled it first so you can delete those styles and add your own).


##Simple Sample Usage

* Download and include `foursquare_suggest.js`

* Call the `fs_suggest()` method as in the following example

```javascript
$('#my_input').fs_suggest({
	'client_id'		: 'YOUR_CLIENT_ID',
	'client_secret'	: 'YOUR_CLIENT_SECRET',
	'll' : '37.787920,-122.407458', 
	'limit' : 10,
	'radius': 20000
});
```
In the above sample, we took an html input element with the id of `my_input` and called the `fs_suggest()` method to activate the plugin. We also passed some parameters into the plugin, `client_id`, `client_secret`, `ll` (latitude, longitude), `limit` and `radius`. See below for an explanation of supported parameters.

You can then bind the `venue_selected.fq_suggest` event on `my_input` so you can do something when a venue is selected. This is triggered by the mouse click event on a venue link and by pressing <enter> on the input.

```javascript
$('input#place_foursquare_venue').on('venue_selected.fq_suggest', function(event, data) {
	venue = data.venueNode;
	
	// Do something with venue
	console.log("Clicked on " + venue.data('name'));
});
```
The `venueNode` is the venue link, which contains the following data attributes:

* `data-name`    - venue name
* `data-city`    - venue city (can be blank)
* `data-address` - venue address (can be blank)
* `data-lat`     - venue latitude
* `data-lng`     - venue longitude
* `data-id`      - venue id (can be blank (?))

##Supported Parameters:

* `client_id` - Foursquare API Client ID
* `client_secret` - Foursquare API Client Secret
* `ll` - A Latitude/Longitude pair
* `limit` - The number of results you want to get
* `radius` - Radius of search centred in `ll` - maximum is 80000 (80Km)

##Contribute

This is a work in progress, suggestions and changes welcome. To contribute.

* fork it
* change it
* submit a pull request
