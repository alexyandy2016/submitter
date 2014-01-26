A jquery plugin for submit form with no refresh.

## Installation

Include files:

```html
<script src="/path/to/jquery.js"></script><!-- jQuery is required -->
<script src="/path/to/jquery.submitter.js"></script>
```

## Usage

Demo form:

```html
<form id="form" action="handle.html" method="post" enctype="multipart/form-data">
	<input name="text" type="text">
	<input name="file" type="file">
	<button type="submit">Submit</button>
</form>
```
Init with options:

```javascript
$("#form").submitter({
	resetAfterDone: true,
	messages: {
		start: "Submit start.",
		done: "Submit done.",
		fail: "Submit fail.",
		end: "Submit end."
	},
	ajaxOptions: { // options for $.ajax()
		cache: false,
		dataType: "json"
		// ...
	},

	isValidated: function() {
		// validate before submit, return true to allow submit
		return true; 
	},

	start: function() {
		console.log(this.messages.start);
	},

	done: function(data) {
		// data: the handle result from server client
		console.log(this.messages.done);
	},

	fail: function() {
		console.log(this.messages.fail);
	},

	end: function() {
		console.log(this.messages.end);
	}
});
```