# Trailhead Rest API

A Golang app that runs on Heroku to make callouts to `trailhead.me/` and displays returned JSON data. That data can then be used in other applications. You can also clone and deploy this to your own Heroku instance.

> Note that in order to retrieve data for a specific Trailhead User, they must have their profile set to public.

## Installation

Create a new Heroku app and push the source up. See the [Heroku docs](https://devcenter.heroku.com/articles/getting-started-with-go#deploy-the-app) for how to deploy the app.

``` bash
$ heroku create
$ git push heroku master
$ heroku open
```

If you have [Go](https://golang.org/doc/install) installed, you can run it locally by using the `run` command on `main.go`.

``` bash
$ go run main.go
```

## Usage

This app has a few different endpoints for accessing public Trailhead data.

### Profile Data

``` text
https://trailhead-rest-api.herokuapp.com/trailblazer/<trailhead_handle>
```

This endpoint returns information about skills learned, counts of badges, points, trails, points til next rank, and rank. [Example](https://trailhead-rest-api.herokuapp.com/trailblazer/michalbogusz)

``` text
https://trailhead-rest-api.herokuapp.com/trailblazer/<trailhead_handle>/profile
```

This endpoint returns public Profile information found on trailblazer.me like about me data, company info, name, and profile/banner photo. [Example](https://trailhead-rest-api.herokuapp.com/trailblazer/michalbogusz/profile)

### Badge Data

``` text
https://trailhead-rest-api.herokuapp.com/trailblazer/<trailhead_handle>/badges
```

This endpoint returns badges earned by the Trailblazer. The API only gives a max of 30 at a time. You can filter badges by sending a string at the end of the URL. Possible filter values are: all, module, superbadge, event, and project. [Example](https://trailhead-rest-api.herokuapp.com/trailblazer/michalbogusz/badges/superbadge)

``` text
https://trailhead-rest-api.herokuapp.com/trailblazer/<trailhead_handle>/badges/<offset>
```

Add an offset to the end of the filter will allow you to offest your badge query by that many. For example, because the API only returns 30 at a time, `/badges/module` will only get you the 30 most recent badges of type module. To get the next 30 you would call `/badges/module/30` to offset the query and return the next 30 badges. [Example](https://trailhead-rest-api.herokuapp.com/trailblazer/michalbogusz/badges/module/30)

### Certifications Data

``` text
https://trailhead-rest-api.herokuapp.com/trailblazer/<trailhead_handle>/certifications
```

This endpoint returns Certifications the Trailblazer has achieved. [Example](https://trailhead-rest-api.herokuapp.com/trailblazer/michalbogusz/certifications)

### Thanks
Thanks to @meruff.

Original data from github.com/meruff/go-trailhead-leaderboard-api
