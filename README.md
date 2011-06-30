# Omniauth for Sinatra (with CouchDB)

This is a template for launching Sinatra apps quickly and easily, using [OmniAuth](https://github.com/intridea/omniauth) as the authentication protocol. It differs from most of the "use Twitter with Sinatra" code bases, as it incorporates sessions and a User model in CouchDB. This means your user should remain logged in as long as your server stays live.

The instructions here assume you're using Twitter, but you can use any auth provider handled by OmniAuth.

This page is mostly come from omniauth-for-sinatra from charliepark (https://github.com/charliepark/omniauth-for-sinatra), I just make it runnable on Heroku and change the persistence from DataMapper to CouchRestModel.

Once you have your auth codes, getting a new Sinatra app with authentication working is simply a matter of copying the app.rb file from here into a new directory, pasting in your auth codes, and then starting in on your app's code. It just works.

## Getting Started Instructions

### 1. Create Heroku apps with Cloudant support

	heroku create <your-app-name-here>
	heroku addons:add cloudant:oxygen
	
This will create a new app on heroku, and install free Cloudant Oxygen addon. The CouchDB is configured automatically and the DB URL is added to environment variable "CLOUDANT_URL"

### 2. Get your Twitter Auth Keys

At Twitter, [register for a new app](https://dev.twitter.com/apps/new). Note the Consumer Key and Consumer Secret strings it gives you.

### 3. Enter your Auth Keys to Heroku

	heroku config:add TWITTER_CONSUMER_KEY=<consumer_key> TWITTER_CONSUMER_SECRET=<consumer_secret>

This will add the consumer key and secret to your Heroku app.

### 4. Deploy

    git push heroku master

If everything goes right, the commit will be pushed to Heroku. Fired up http://<your-app-name-here>.heroku.com and test your new app with Twitter authentication!

## Note

The app can be run locally. Just set the CLOUDANT_URL, TWITTER_CONSUMER_KEY and TWITTER_CONSUMER_SECRET. You are good to go.

Note that **you cannot use shotgun to test your app**, as you'll need sessions to persist in order to stay logged in, and shotgun restarts the server on every request. Starting your app with 'ruby app.rb' should work with no problems.


## Feedback Is Awesome

If you have any suggestion, please send me a message on Twitter [@siuying](http://twitter.com/siuying).