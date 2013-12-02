# Little Printer Push API example (Python)

This is an example publication written in Python using the [Flask framework](http://flask.pocoo.org/) framework.

This example expands on the Hello World example, and demonstrates how to use the Push API to send messages directly to subscribed Little Printers.


## Configuration

This example requires a Redis server running in order to store the data about subscriptions. If no URL is supplied, then it will use a local server with no authentication.

You will need to get the BERG Cloud OAuth authentication tokens from the page for your newly-created Little Printer publication (in [Your publications](http://remote.bergcloud.com/developers/publications/)).  

Configuration details can be set either in a `settings.cfg` file (copy `settings.cfg.example`) or in environment variables.

`settings.cfg` should be like:

    BERGCLOUD_CONSUMER_TOKEN = 'yourConsumerToken'
    BERGCLOUD_CONSUMER_TOKEN_SECRET = 'yourConsumerTokenSecret'
    BERGCLOUD_ACCESS_TOKEN = 'yourAccessToken'
    BERGCLOUD_ACCESS_TOKEN_SECRET = 'yourAccessTokenSecret'

If you have a Redis URL, add that:

	REDIS_URL: redis://username:password@your.redis.server:12345

If using enivronment variables, these are the same:
	
	BERGCLOUD_CONSUMER_TOKEN
	BERGCLOUD_CONSUMER_TOKEN_SECRET
	BERGCLOUD_ACCESS_TOKEN
	BERGCLOUD_ACCESS_TOKEN_SECRET

And the Redis URL:

	REDIS_URL

By default the application is run with `DEBUG=False`. To change this add a line
like this to `settings.cfg` or as an enivironment variable:

    DEBUG = True

Flask can be installed using [pip](https://pypi.python.org/pypi/pip):

	$ pip install -r requirements.txt

If a `settings.cfg` file is present, its contents will be used in place of any environment variables.


## Run it

Run the server with:

	$ python publication.py

You can then visit these URLs:

	* `/icon.png`
	* `/meta.json`
	* `/sample/`
	* `/push/`

The `/push/` page lets you send a greeting to all subscribed Little Printers.

In addition, the `/validate_config/` URL should accept a POST request with a field named `config` containing a string like:

	{"lang":"english", "name":"Phil", "endpoint": "http://api.bergcloud.com/v1/subscriptions/2ca7287d935ae2a6a562a3a17bdddcbe81e79d43/publish", "subscription_id": "2ca7287d935ae2a6a562a3a17bdddcbe81e79d43"}

but with a unique `endpoint` and `subscription_id`.


----

BERG Cloud Developer documentation: http://remote.bergcloud.com/developers/


