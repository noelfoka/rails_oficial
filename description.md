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
### Default route

```ruby
root "articles#index"
```
## MVC

### Generating a model

```ruby
rails g model Article title:string body:text
```
### Database migration

```bash
rails db:create

rails db:migrate
```

### Using model to interact with the database

```bash
rails generate model Article title:string body:text
```
