<h1>Alpha-Blog : Complete Ruby on Rails Developer Udemy course.</h1>

<h3>Heroku setup</h3>

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

<h4>Create migration</h4>
<p>$ rails g migration create_articles title:string description:text</p>
<h4>Rollback a migration</h4>
<p>$ rake db:rollback</p>

<h3>Add a migration to an existing table</h3>
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
