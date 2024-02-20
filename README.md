## Members only

### The motto of this assignment
 * To create basic authentication form (I use Devise gem)
 * If the user sign_in we have to display respective author name in the posts
 * Otherwise it will only display the posts without author name
 * without sign_in user cann't create post

### Devise authentication
```
bundle add devise
rails generate devise:install
rails generate devise User
rails db:migrate
```
### **Post** Controller, Model creation

```
rails generate controller Users new create index --->[For this these 3 controller actions are enough]
rails geenrate model User title:string content:text

```

### Filter addition
I added a filter in the post controller this will prevent the user to create a post without sign_in
```
before_action :authenticate_user! only: [:new, :create]
```
### Connection between post & user model

Right now there is no way of communication between both user and post models.
To make we are adding a column(user_id) in the post model with reference to the user

```
rails generate migration AddUserIdToPosts user:references

```
### post index logic
```
<h6>
  This is created by <%= User.find_by(id: post.user_id).email%>
  <%end%>
</h6>
```

[Screencast from 02-20-2024 07:38:51 PM.webm](https://github.com/Malavi1/Members-only/assets/112646623/ae5b73a1-8355-41fd-b7f1-5116b52d532a)



