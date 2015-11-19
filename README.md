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

<h2>Rails console</h2>
<p>  article.errors.any?<br>
 article.errors.full_messages</p>

 <h2>Routes</h2>
 <p>add resources :articles</p>
