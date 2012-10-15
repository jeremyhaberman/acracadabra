# acracadabra

Rails backend for [ACRA](https://code.google.com/p/acra/)

## Contents

* [Overview](#overview)
* [Dependencies](#dependencies)
* [Development Setup](#setup)
* [Deploying to Heroku](#deployment)
* [API Documentation]
* [Config Vars]

<a name="overview"></a>
## Overview

This is a Rails backend for [ACRA](https://code.google.com/p/acra).

<a name="dependencies"></a>
## Dependencies

* See the Gemfile
* Ruby 1.9.3
* Rails 3.2.8
* PostgreSQL

<a name="setup"></a>
## Setup

### Grab the Source

1. [Fork the repo](https://github.com/livefront/acracadabra/fork_select)

2. Checkout the source

        $ git clone git@github.com:<your_account>/acracadabra.git
        $ cd acracadabra
        $ git checkout -t origin/stable
        $ git checkout master

### App Setup

1. Install dependencies:

        $ bundle install

2. Set up RSpec

        $ rails generate rspec:install  

3. Run unit tests:

        $ rspec

4. Specify report recipients in the `.env` file.  Example:

        RECIPIENTS=jeremy@livefront.com

5. Fire it up:

        $ foreman start

    [Foreman](https://github.com/ddollar/foreman) is used because of its ability to easily set environment variables with the `.env` file. 

5. Confirm the dev server is running and configured properly

    Load `http://localhost:5000` in your browser.

<a name="deployment"></a>
## Deploying to Heroku

### One-time setup

1. Create the app

        $ heroku create --stack cedar

1. Add Heroku add-on(s)

        $ heroku addons:add sendgrid:starter

2. Set Heroku config variable for report recipients

        $ heroku config:add RECIPIENTS=<email_address>

### Deployment

    $ git push heroku master
    $ heroku ps:restart
