+++
# Contact widget.

date = "2016-04-20T00:00:00"
draft = false

title = "Contact"
subtitle = ""
widget = "contact"

# Order that this section will appear in.
weight = 70

# Automatically link email and phone?
autolink = true

+++

<form action="https://formspree.io/website@marceldehaas.com" method="POST">
	<input type="hidden" name="_next" value="https://marceldehaas.com/sent" />
	<input type="hidden" name="_subject" value="New submission!" />
	<input type="text" name="_gotcha" style="display:none" />
    Name: <input type="text" name="name" /><br />
    Email: <input type="email" name="_replyto" placeholder="Your email" /><br />
	Message:<br />
	<textarea name="message" cols=52 rows=10></textarea><br />
    <input type="submit" value="Send" />
</form>