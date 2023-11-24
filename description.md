# Step to build my App

## Getting started

### Create rails app

```bash
rails new ./ --database=postgresql
```
### Connect to database

- Add username and password for my postgresql
- Connect by add this command: `rails db:create`.

### Add the route
To add tho route, let follow this directory `config/routes.rb` and write this code:
```ruby
get "/articles", to: "articles#index"
```
### Add controller, model, and view

To make it, let generate this code:

```bash
rails g controller articles index --skip-routes
```
