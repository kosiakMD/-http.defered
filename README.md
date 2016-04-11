# -http.promise

"dependencies": {
    "jquery": ">1.5"
  }

Mozilla "$http" plugin + jQuery.Deferred (instead original .Promise);

jQuery and Angular AJAX-methods are slower then clear XHHR, so hthe best short way to use it I found here https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/Synchronous_and_Asynchronous_Requests
BUT, clear JS Promise is not crossbroswer's, so it was replaced by jQuery.Deferred https://api.jquery.com/category/deferred-object/

for Example:

<code>
$http( "settings.json").get()//load json file
	.then(
		function(data){//if data load Good (XHR)
		  ...
		},
		function(data, url){//if data load fail (XHR)
  		...
		}
	);
});
</code>
