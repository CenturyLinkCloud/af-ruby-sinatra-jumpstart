# AppFog Ruby Sinatra Jumpstart

## Introduction

The AppFog Ruby Sinatra Jumpstart is a sample application that can be used to get started quickly with a new Sinatra web application on AppFog.

## Getting Started

### Installing Bundler and trying the app locally

This sample application uses Bundler to manage dependencies. If you want to just push to AppFog without trying the application locally, just skip to the next section.
To install Bundler go the root of the project and do:
```
$ gem install bundle
Successfully installed bundler-1.10.3
Parsing documentation for bundler-1.10.3
Done installing documentation for bundler after 2 seconds
1 gem installed
```

Then, install all the dependencies with the `bundle install` command.
Once all the libraries are installed, run the app by doing `thin start -R config.ru`.
This will start a server in the port 3000. If you go to http://localhost:3000 you should see the AppFog web page displaying.

### Pushing to AppFog

To deploy the application, run the following from the top-level project directory:

```
$ cf push
```

Since the manifest.yml file sets the name of the application to `${random-word}`, the name of the application will be generated during the deployment process. Here is example output of the application deployment using `cf push`:

```
$ cf push
Using manifest file /Users/demo/projects//af-ruby-sinatra-jumpstart/manifest.yml

Creating app raging-badger in org DEMO / space Dev as Demouser...
OK

Using route raging-badger.useast.appfog.ctl.io
Binding raging-badger.useast.appfog.ctl.io to raging-badger...
OK

Uploading raging-badger...
Uploading app files from: /Users/demo/projects//af-ruby-sinatra-jumpstart
Uploading 13.4K, 8 files
Done uploading               
OK

Starting app raging-badger in org DEMO / space Dev as Demouser...
-----> Downloaded app package (8.0K)
-------> Buildpack version 1.4.1
-----> Compiling Ruby/Rack
-----> Using Ruby version: ruby-2.2.2
-----> Installing dependencies using 1.7.12
       Running: bundle install --without development:test --path vendor/bundle --binstubs vendor/bundle/bin -j4 --deployment
       Fetching gem metadata from https://rubygems.org/..........
       Installing daemons 1.2.2
       Installing rack 1.6.1
       Using bundler 1.7.12
       Installing tilt 2.0.1
       Installing rack-protection 1.5.3
       Installing sinatra 1.4.6
       Installing eventmachine 1.0.7
       Installing thin 1.6.3
       Your bundle is complete!
       Gems in the groups development and test were not installed.
       It was installed into ./vendor/bundle
       Bundle completed (20.39s)
       Cleaning up the bundler cache.

-----> Uploading droplet (18M)

1 of 1 instances running

App started


OK

App raging-badger was started using this command `bundle exec thin start -p $VCAP_APP_PORT -R config.ru`

Showing health and status for app raging-badger in org DEMO / space Dev as Demouser...
OK

requested state: started
instances: 1/1
usage: 128M x 1 instances
urls: raging-badger.useast.appfog.ctl.io
last uploaded: Thu Jun 11 20:03:27 UTC 2015

     state     since                    cpu    memory          disk          details   
#0   running   2015-06-11 05:04:10 PM   0.0%   48.3M of 128M   72.4M of 1G 
```

Once the application is running, copy the value for `urls:`, in the case above `raging-badger.useast.appfog.ctl.io`, and go to that URL in a browser. You should see a page that looks like:

<img src="https://raw.githubusercontent.com/CenturyLinkCloud/af-static-jumpstart/master/images/welcome-to-appfog-screenshot.png"/>
 
## Customizing the app

### Knowing where the code is

* Web page: `public/index.html`.
* Application Controller: `lib/server.rb`.

### Deploying Ruby apps to AppFog

A very useful read is [here](https://to_be_done/). This will give you an overview of the general process used to deploy Ruby applications to AppFog.

### Moving forward

You could add a more routes in `lib/server.rb`, maybe like this one:

```
get '/hi' do
  "Hi there!"
end
```

There is a very good documentation and a lot of good examples of Sinatra applications [here](http://www.sinatrarb.com/intro.html).