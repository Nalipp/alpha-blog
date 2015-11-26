<h1>Udemy Alpha-Blog : Complete Ruby on Rails Developer - course notes</h1>

<h2>Heroku setup</h2>

<p>move:<br>
gem 'sqlite3'</p>

<p>group :development, :test do<br>
gem 'sqlite3'<br>
end</p>

<p>add:<br>
group :production do<br>
  gem 'pg'<br>
  gem 'rails_12factor'<br>
end</p>

<p>$ heroku create<br>
$ git push heroku master<br>
$ heroku rename [new-name]</p>

<h4>After adding migrations</h4>
<p>$ heroku run rake db:migrate</p>

<h2>Models and migrations</h2>

<h4>Create migration</h4>
<p>$ rails g migration create_articles title:string description:text</p>

<h4>Rollback a migration</h4>
<p>$ rake db:rollback</p>

<h4>Add a migration to an existing table</h4>
<p>$ rails g migration add_description_to_articles</p>
<p>class AddDescriptionToArticles < ActiveRecord::Migration<br>
  def change<br>
    add_column :articles, :description, :text<br>
    add_column :articles, :created_at, :datetime<br>
    add_column :articles, :updated_at, :datetime<br>
  end<br>
end</p>

<h4>Create a model with timestamps</h4>
<p>$ rails generate model Article title:string description:text</p>

<h2>Validations</h2>
<p>class Article < ActiveRecord::Base<br>
  validates :title, presence: true, length: { minimum: 3, maximum: 50 }<br>
  validates :description, presence: true, length: { minimum: 10, maximum: 300 }<br>
end</p>

<p>class User < ActiveRecord::Base<br>
before_save { self.email = email.downcase }</br>
validates :username, presence: true,</br>
          uniqueness: { case_sensitive: false },</br>
          length: { minimum: 3, maximum: 25 }</br>
VALID_EMAIL_REGEX = /\A[\w+\-.]+@[a-z\d\-.]+\.[a-z]+\z/i</br>
validates :email, presence: true, length: { maximum: 105 },</br>
          uniqueness: { case_sensitive: false },</br>
          format: { with: VALID_EMAIL_REGEX }</p>

<h2>Rails console</h2>
<p>$ article.errors.any?<br>
$ article.errors.full_messages<br>
$ user.authenticate("password")</p>

 <h2>Routes</h2>
 <p>add resources :articles</p>

<h2>Git branch</h2>
<p>$ git branch<p>

<h4>Create a feature branch</h4>
<p>$ git checkout -b [branch name]<br>
$ git checkout master<br>
$ git merge [branch name]</p>

<h4>Delete a feature branch</h4>
<p>git branch -d [branch name]</p>

<h2>Create password digest</h2>

<h4>update gemfile</h4>

<p>gem 'bcrypt'<br>
$ bundle install --without production</p>

<h4>add to password_digest to User migration</h4>

<p>$ rails g migration add_password_digest_to_users<br><br>

def change<br>
  add_column :users, :password_digest, :string<br>
end<br>

$rake db:migrate</p>

<h4>update user.rb model</h4>

<p>add:<br>
 has_secure_password</p>

 <h2>Add paginate</h2>

 <h4>Gemfile</h4>

 <p>gem 'will_paginate', '3.0.7'<br>
 gem 'bootstrap-will_paginate', '0.0.10'</p>

<h4>articles_controller.rb</h4>

<p>def index<br>
    @articles = Article.paginate(page: params[:page], per_page: 5)<br>
end</p>

<h4>articles/index.html.erb</h4>

<p><div align="center"><br>
  <%= will_paginate %><br>
</div></p>
