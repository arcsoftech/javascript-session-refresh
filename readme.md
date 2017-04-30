# Javascript Session Refresh

This script auto refreshes your logged in session by detecting various events (mouse move, mouse click, touchscreen, typing) which sends an Ajax call to a page that manages your sessions without reloading a page you're currently on.

If you don't do anything on a page for a while, an error message will appear letting you know that you'll be logged out soon. There is an option to display a count down progress bar with amount of seconds left before automatic logout takes place. When an error message appears, web browser's tab will flash an alert that says "you're about to be logged out!" which is useful when you're in another web browser tab.

Session refresh has been inspired by https://github.com/orangehill/bootstrap-session-timeout but with some modification to the code.

Title alert has been inspired by https://github.com/heyman/jquery-titlealert.


## How to use it

There are two implementations: for Bootstrap'ed websites and non-Bootstrap'ed ones.

### Bootstrap'ed

Add links to the ```<head>``` section of your HTML document or at the bottom of ```<body>``` section

```
<link rel="stylesheet" href="css/bootstrap.min.css">
<script src="js/jquery.min.js"></script>
<script src="js/bootstrap.min.js"></script>
<script src="js/jquery-titlealert.js"></script>
```

Add this snippet to the bottom of your ```<body>``` tag (below the links mentioned above)
```
<script src="js/bootstrap-session-timeout.js"></script>
<script>
	$.sessionRefresh({
		keepAliveUrl: 'keepsessionalive.html',
		logoutUrl: 'logout.html',
		redirUrl: 'redirect.html',
		warnAfter: 5000, // 5 seconds
		redirAfter: 20000, // 20 seconds
		keepAliveInterval: 12000, // 12 seconds
		countdownBar: true,
		tabFlashMessage: 'You are about to be logged out!'
	});
</script>
```

Save your document and test.

### non-Bootstrap'ed

Add links to the ```<head>``` section of your HTML document or at the bottom of ```<body>``` section

```
<link rel="stylesheet" href="css/styles.css">
<script src="js/jquery.min.js"></script>
<script src="js/modal-window.min.js"></script>
<script src="js/jquery-titlealert.js"></script>
```

Add this snippet to the bottom of your ```<body>``` tag (below the links mentioned above)
```
<script src="js/bootstrap-session-timeout.js"></script>
<script>
	$.sessionRefresh({
		keepAliveUrl: 'keepsessionalive.html',
		logoutUrl: 'logout.html',
		redirUrl: 'redirect.html',
		warnAfter: 5000, // 5 seconds
		redirAfter: 20000, // 20 seconds
		keepAliveInterval: 12000, // 12 seconds
		countdownBar: true,
		tabFlashMessage: 'You are about to be logged out!'
	});
</script>
```

Save your document and test.

## Content of the repository

There are 2 folders in this project - **bootstrap** and **non-bootstrap**. Files in **bootstrap** folder utilize Bootstrap framework and will display modal alert window with a countdown bar. Files in **non-bootstrap** folder use custom CSS styles and stripped down modal alert from bootstrap.

## Possible limitations

In case you have an iframe element that occupies a large area of your website and the session auto refresh is running on the "parent" page and not in the iframe, the javascript session refresh script will not pick up on various events (mouse scroll, mouse click, typing on a keyboard) and your session will not be refreshed.
