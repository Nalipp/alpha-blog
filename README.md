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
