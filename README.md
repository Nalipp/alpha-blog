<h1>Alpha-Blog : Complete Ruby on Rails Developer Udemy course.</h1>

<h2>Heroku setup</h2>

<h4>move:</h4>
<p>gem 'sqlite3'</p>

<p>group :development, :test do</p>
<p>end<p>

<h4>add:</h4>
<p>group :production do</p>
  <p>gem 'pg'</p>
  <p>gem 'rails_12factor'</p>
<p>end</p>

<p>$ heroku create</p>
<p>$ git push heroku master</p>
<p>$ heroku rename [new-name]</p>
<p></p>

<h2>Models and migrations<h2>

<h4>Create migration</h4>
<p>$ rails g migration create_articles title:string description:text</p>
<h4>Rollback a migration</h4>
<p>$ rake db:rollback</p>

<h4>Add a migration to an existing table</h4>
<p>$ rails g migration add_description_to_articles</p>
<p>class AddDescriptionToArticles < ActiveRecord::Migration</p>
  <p>def change</p>
    <p>add_column :articles, :description, :text</p>
    <p>add_column :articles, :created_at, :datetime</p>
    <p>add_column :articles, :updated_at, :datetime</p>
  <p>end</p>
<p>end</p>

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
