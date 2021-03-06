# Sample_app

## Chapter 1:

#### Doc
[Learn enough to be dangerous](https://www.learnenough.com)

#### MVC
![](https://user-images.githubusercontent.com/18675907/28787437-69bda5f6-7646-11e7-9094-f3ab10af2efd.png)

#### Git config
```
git config --global user.name "HoanKi"
git config --global user.email "hoanki2212@gmail.com"
```

```
New ssh key
  ssh-keygen -t rsa -C "hoanki2212@gmail.com"

Find ssh key at: ~/.ssh/id_rsa.pub
  ssh-rsa AAxxxBBBB
  hoanki2212@gmail.com

```

#### Deploy to heroku

```
Use gem pg to deploy database in heroku host.

  group :development, :test do
    gem 'sqlite3', '1.3.13'
  end

  group :production do
    gem 'pg', '0.20.0'
  end
```

```
bundle install --without production
```

[How to deploy to heroku](https://devcenter.heroku.com/articles/heroku-cli)

Some command:
```
Install:  wget -qO- https://cli-assets.heroku.com/install-ubuntu.sh | sh
Version:  heroku version
Login:    heroku login
SSH key:  heroku keys:add
New app:  heroku create
Rename:   heroku rename new_name
Push:     git push heroku master #(master of local to master of heroku)
          git push heroku develop:master #(develop of local to master of heroku)
```

## Chapter 2:

#### Url
```
HTTP Request  Url           Action          Purpose

GET           /users        index           show all users
POST          /users        create          new users
GET           /users/1      show            show uses with id 1
GET           /users/new    new             make new user
GET           /users/1/edit edit            edit user with id 1
PATCH         /users/1      update          update user with id 1
DELETE        /users/1      detele          delete users with id 1
```

#### MVC

![](https://user-images.githubusercontent.com/18675907/28814626-5843e5a8-766c-11e7-81be-49895750bfa5.png)

#### Association
```
>> first_user = User.first
=> #<User id: 1, name: "Michael Hartl", email: "michael@example.org",
created_at: "2016-05-15 02:01:31", updated_at: "2016-05-15 02:01:31">

>> first_user.microposts
=> [#<Micropost id: 1, content: "First micropost!", user_id: 1, created_at:
"2016-05-15 02:37:37", updated_at: "2016-05-15 02:37:37">, #<Micropost id: 2,
content: "Second micropost", user_id: 1, created_at: "2016-05-15 02:38:54",
updated_at: "2016-05-15 02:38:54">]

>> micropost = first_user.microposts.first    # Micropost.first would also work.
=> #<Micropost id: 1, content: "First micropost!", user_id: 1, created_at:
"2016-05-15 02:37:37", updated_at: "2016-05-15 02:37:37">

>> micropost.user
=> #<User id: 1, name: "Michael Hartl", email: "michael@example.org",
created_at: "2016-05-15 02:01:31", updated_at: "2016-05-15 02:01:31">
>> exit
```

##### OOP
![](https://user-images.githubusercontent.com/18675907/29394988-212c174c-8338-11e7-9854-52b9cd956d07.png)

![](https://user-images.githubusercontent.com/18675907/29394994-258b8c78-8338-11e7-82c8-371dc4571c2f.png)


## Chapter 3:

#### Generate controller and model

```
rails generate controller StaticPages home help

rails destroy controller StaticPages home help

rails db:migrate

rails db:rollback

rails db:migrate VERSION=0

rails s -b $IP -p $PORT
```

```
The hypertext transfer protocol (HTTP) defines the basic operations GET, POST, PATCH, and DELETE. These refer to operations between a client computer (typically running a web browser such as Chrome, Firefox, or Safari) and a server (typically running a webserver such as Apache or Nginx). (It’s important to understand that, when developing Rails applications on a local computer, the client and server are the same physical machine, but in general they are different.) An emphasis on HTTP verbs is typical of web frameworks (including Rails) influenced by the REST architecture, which we saw briefly in Chapter 2 and will start learning more about in Chapter 7.

GET is the most common HTTP operation, used for reading data on the web; it just means “get a page”, and every time you visit a site like http://www.google.com/ or http://www.wikipedia.org/ your browser is submitting a GET request. POST is the next most common operation; it is the request sent by your browser when you submit a form. In Rails applications, POST requests are typically used for creating things (although HTTP also allows POST to perform updates). For example, the POST request sent when you submit a registration form creates a new user on the remote site. The other two verbs, PATCH and DELETE, are designed for updating and destroying things on the remote server. These requests are less common than GET and POST since browsers are incapable of sending them natively, but some web frameworks (including Ruby on Rails) have clever ways of making it seem like browsers are issuing such requests. As a result, Rails supports all four of the request types GET, POST, PATCH, and DELETE.
```

```
  html.reb: Embedded Ruby: Nhúng ruby vào html

  (The distinction between the two types of embedded Ruby is that <% ... %> executes the code inside, while
  <%= ... %> executes it and inserts the result into the template.) The resulting page is exactly the same as before, only now the variable part of the title is generated dynamically by ERb.

  This code arranges to include the application stylesheet and JavaScript, which are part of the asset pipeline (Section 5.2.1), together with the Rails method csrf_meta_tags, which prevents cross-site request forgery (CSRF), a type of malicious web attack.

```

## Chapter 4

#### Load css & js
```
<%= stylesheet_link_tag 'application', media: 'all',
                                      'data-turbolinks-track': 'reload' %>
```

This uses the built-in Rails function stylesheet_link_tag (which you can read more about at the [Rails API](http://api.rubyonrails.org/classes/ActionView/Helpers/AssetTagHelper.html#method-i-stylesheet_link_tag)) to include application.css for all [media types](https://www.w3.org/TR/CSS2/media.html) (including computer screens and printers). To an experienced Rails developer, this line looks simple, but there are at least four potentially confusing Ruby ideas: built-in Rails methods, method invocation with missing parentheses, symbols, and hashes. We’ll cover all of these ideas in this chapter.

![](https://user-images.githubusercontent.com/18675907/29450135-a3857b62-8427-11e7-9699-a0b3da4a09d5.png)


![](https://user-images.githubusercontent.com/18675907/29450293-59d930e8-8428-11e7-8b51-2ab7ca291af5.png)


## Chapter 5

#### Sass & css

Sas has many form of expression, ex: scss

Css -> Sass

```
.center {
  text-align: center;
}

.center h1 {
  margin-bottom: 10px;
}

==>

.center {
  text-align: center;
  h1 {
    margin-bottom: 10px;
  }
}
```

```
#logo {
  float: left;
  margin-right: 10px;
}

#logo:hover {
  color: #fff;
  text-decoration: none;
}

==>

#logo {
  float: left;
  margin-right: 10px;
  &:hover {
    color: #fff;
    text-decoration: none;
  }
}
```
