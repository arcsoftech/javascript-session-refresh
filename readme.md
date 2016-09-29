#Javascript Session Refresh

This script auto refreshes your logged in session by detecting various events (mouse move, mouse click, touchscreen, typing) which then sends an Ajax call to a page that manages your sessions without reloading a page that you're currently on.

If you don't do anything for a while, you'll see an error message with a countdown timer indicating that you'll be logged out soon. Additionally, there is a title alert function which will "flash" a message on the tab when the error message is displayed.

Session refresh has been inspired by https://github.com/orangehill/bootstrap-session-timeout but with some modification to the code.

Title alert has been inspired by https://github.com/heyman/jquery-titlealert.


##How to use it

Add links to the ```<head>``` section of your HTML document

```
<link rel="stylesheet" href="css/bootstrap.min.css">
<script src="js/jquery.min.js"></script>
<script src="js/bootstrap.min.js"></script>
<script src="js/jquery-titlealert.js"></script>
```

Add this snippet to the bottom of your ```<body>``` tag
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

##Content of the repository

There are 2 folders in this project - **bootstrap** and **non-bootstrap**. Files in **bootstrap** folder utilize Bootstrap framework and will display modal alert window with a countdown bar. Files in **non-bootstrap** folder use custom CSS styles and Javascript alert window.

Currently I'm adding **bootstrap folder** as I'm working on a demo for non-bootstrap page.

##Possible limitations

In case you have an iframe element that occupies a large area of your website and the session auto refresh is running on the "parent" page and not in the iframe, the javascript session refresh script will not pick up on various events (mouse scroll, mouse click, typing on a keyboard) and your session will not be refreshed.