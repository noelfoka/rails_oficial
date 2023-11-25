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

```bash
rails generate model Article title:string body:text
```

### Using model to interact with the database

Type this command: `rails console`

Inside the console, We can:

- Add a new article: 
```bash
article = Article.new(title: "Hello rails", body: "I am on rails rails")
```
- Save the new article:
```bash
article.save
```
- See this article: `article`
- Find the article by `id`:
```ruby
Article.find(1)
```

### Showing a list of A rticle

- Inside our controller, add this command:
```ruby
@article = Article.all
```
- Inside your `views/articles/index.html.erb` add this code:

```ruby
<ul>
    <% @article.each do |article| %>
        <li>
            <%= article.tile%>
        </li>
    <% end %>
</ul>
```

## CRUD

### showing a single article

- **Routes**
Add this route
```ruby
get "/articles/:id", to: "articles#show"
```
- **New action in articles_controller**

```ruby
def show
    @article = Article.find(params[:id])
end
```
- **Views**
In `views/article`, create `show.html.erb` file and add the the single article by adding title and body

### Create New Article

- **Controller**

In `controller/articles_controller.rb` create new action method called `new`:
```ruby
def new
    @article = Article.new
end
``` 
- **Views**

In `views` directory, create a new file `show.html.erb` and write this code:
```ruby
<h1>New Article</h1>

<%= form_with model: @article do |form| %>
    <div>
        <%= form.label :title %><br>
        <%= form.text_field :title %>
        <% @article.errors.full_messages_for(:title).each do |message| %>
            <div>
                <%= message %>
            </div>
        <% end %>
    </div>

    <div>
        <%= form.label :body %><br>
        <%= form.text_area :body %>
        <% @article.errors.full_messages_for(:body).each do |message| %>
            <div>
                <%= message %>
            </div>
        <% end %>
    </div>

    <div>
        <%= form.submit %>
    </div>
<% end %>
```

### Edit and Update

