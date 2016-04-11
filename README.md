# $http (AJAX) and Deffered (Promise)

"dependencies": {
    "jquery": ">1.5"
  }

Clear JavaScript XMLHttpRequest "$http"-plugin + jQuery.Deferred (instead original Promise);

jQuery and Angular AJAX-methods are slower then clear XHHR, so the best short way to use it I found here in MDN https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise#Example_using_new_XMLHttpRequest()

BUT, clear JS Promise is not crossbroswer's, so it was replaced by jQuery.Deferred https://api.jquery.com/category/deferred-object/

for Example:

```javascript
$http( "settings.json").get()//load json file
	.then(
		function(data){//if loading success
		  ...
		},
		function(data, url){//if loading failed
  		...
		}
	);

// B-> Here you define its functions and its payload
var mdnAPI = 'https://developer.mozilla.org/en-US/search.json';
var payload = {
  'topic' : 'js',
  'q'     : 'Promise'
};

var callback = {
  success : function(data){
     console.log(1, 'success', JSON.parse(data));
  },
  error : function(data){
     console.log(2, 'error', JSON.parse(data));
  }
};
// End B

// Executes the method call 
$http(mdnAPI) 
  .get(payload) 
  .then(callback.success) 
  .catch(callback.error);

// Executes the method call but an alternative way (1) to handle Promise Reject case 
$http(mdnAPI) 
  .get(payload) 
  .then(callback.success, callback.error);

// Executes the method call but an alternative way (2) to handle Promise Reject case 
$http(mdnAPI) 
  .get(payload) 
  .then(callback.success)
  .then(undefined, callback.error);


```
