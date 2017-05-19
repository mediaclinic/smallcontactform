# Small Contact form
> Simple but flexible contact form builder with custom fields, validation and passive antispam.


## Installation

**GitHub** clone into `/plugins` dir:

```sh
git clone https://github.com/jan-vince/smallcontactform
```

**OctoberCMS backend**

Just look for 'Small Contact Form' in search field in:
> Settings > Updates&Plugins > Install plugins

### Permissions

> Settings > Administrators

You can set permissions to restrict access to *Settings > Small Contact form* and to messages list.


## Setup new Contact form

> Settings > Small Contact form

### FORM

* You can set your own CSS class name and general success/error messages.
* Form can be hidden after successfull send.

#### Enable AJAX

By default, sending form will trigger page reload. With AJAX, everything can be done without page reloading which will be more user friendly.    
*If user's browser doesn't support (or has disabled) JavaScript, form will still work with page reloads after send.*

* For AJAX enabled form, before send confirmation dialog can be required.


#### Add Asssets

If you want to start quickly, you can enable Add assets checkbox - and then Add CSS and JS assets.    
This will include necessary styles (Bootstrap, AJAX, October AJAX) and scripts (jQuery, Bootstrap, October AJAX framework and extras).

But you have to include Twig tags ````{% styles %}```` and ````{% scripts %}```` into your layout or page like this:

````html
<html>
	<head>
		{% styles %}
	</head>
<body>

	{% page %}

	{% scripts %}

</body>

</html>
````

### SEND BUTTON

* You can set button class and text.


### FIELDS

Here you can add fields to build your contact (or other) form.

The idea is simple (and solution is so I hope):

* Click to add new field
* Set it's name (this is used for ````<input name="{{name}}" id="{{name}}">````), so it should be lowercase without special characters.
* Set Label if you need one (it is used for descriptive text above input field)
* Set autofocus if you want cursor to automatically jump to this field (if checked more than one field, cursor jumps to first one)
* Add field validation rules:
 * You can add one or more validation rules and error messages for them
 * Error messages will be shown above input field
* You can reorder fields by drag and drop left circle (all fields can be collapsed by pressing Ctrl+click (Cmd+click on MacOS) on arrow in right top corners)


### ANTISPAM

Very simple implementation of passive antispam (inspired by [Nette AntiSpam Control](https://gist.github.com/Michal-Mikolas/2388131)).

The idea behind this is to check how fast is form send and if robots-catching field is filled.

* When allowed, you can set form delay (in seconds) to prevent toot fast form sendind (mostly by robots). You can add custom error message (will be shown in general error message box above form).
* You can add antispam field label and error message for non JavaScript enabled browsers.
 * If JavaScritp is working, antispam field is automatically hidden and cleared.


### EMAIL

Mails can be sent directly or queued ([OctoberCMS queue](https://octobercms.com/docs/services/queues) must be configured!).

Don't forget to configure mail preferences in *Settings > Mail configuration*!

#### Allow autoreply

Email can be send to form sender as confirmation.

* You have to enter email address and name - it will be used as FROM field
* Email subject can be manually added here (or edited in *Settings > Mail templates (code: janvince.smallcontactform::mail.autoreply)*)
* Email TO address and name have to be assigned to form fields (in selections only corresponding field types are shown - if you don't see one, try to check it's type in Fields tab)
 * Message field can be also assigned (and will be saved separatelly into database)

#### Allow notifications

A notification of sent form can be send to provided email address.


## Messages list

All sent data from Contact form are saved and listed in backend Messages list.

If email, name and message fields are asigned on *Settings > Small contact form > Email | Allow autoreply*, they will be saved in separate columns (you can make fields assignment and disallow autoreply if you don't need this function - but assignments will be preserved).

You can click on a record to see all form data. The message will be marked as read.

----
> My thanks goes to:    
> [OctoberCMS](http://www.octobercms.com) team members and supporters for this great system.   
> [Cristina Gottardi](https://unsplash.com/@cristina_gottardi) for her photo.   
> [Fon Awesome](http://fontawesome.io/icons/) for nice icons.


Created by [Jan Vince](http://www.vince.cz), freelance web designer from Czech Republic.
