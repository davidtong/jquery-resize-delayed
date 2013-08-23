(function(){
  var original = {
		eventAdd: $.event.add
	};

	/**
	 * Override the resize event so that it is only called at the end of a resize rather than
	 * hundreds of times on the course of a resize user action
	 */
	$.extend($.event, {
		add: function(elem, types, handler) {
			var originalHandler = handler,
				timeoutID = null;

			// only apply to resize
			if (types.split('.')[0].toLowerCase() === 'resize') {
				// wrap the original handler with a function that manages the delay
				handler = function() {
					if (timeoutID !== null) {
						window.clearTimeout(timeoutID);
					}
					timeoutID = window.setTimeout(originalHandler, 100);
				};
			}

			// call the original function and pass all the arguments
			// formal paramters are directly mapped to the indices of the arguments object in non-strict mode
			return original.eventAdd.apply(this, arguments);
		}
	});
	
})();
