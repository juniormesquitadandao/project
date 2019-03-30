# New Project

## Project

setup
```sh
mkdir project
echo 'gem: --no-rdoc --no-ri' >> project/.gemrc
echo ruby-2.6.2 > project/.ruby-version
echo project > project/.ruby-gemset
\curl https://www.gitignore.io/api/rails > project/.gitignore
cd project
rvm install ruby-2.6.2
cd ../project
gem install rails --version=5.2.3
rails new . --database=postgresql --skip-git --skip-test --skip-system-test --skip-coffee --skip-bundle
```

edit project/Gemfile
```rb
gem 'sassc-rails'
gem 'mini_racer', platforms: :ruby

group :development, :test do
  gem 'rspec-rails', '~> 3.8'
end

group :development do
  gem 'html2slim', require: false
  gem 'bundler-audit', require: false
end

group :test do
  gem 'factory_bot_rails'
  gem 'simplecov', require: false
end

gem 'sprockets'
gem 'sprockets-es6'
gem 'slim-rails'
gem 'paper_trail'
gem 'devise'
gem 'devise-async'
gem 'devise-i18n'
gem 'action_authorizer', '~> 2.0'
gem 'rails-i18n', '~> 5.1'
gem 'oj'
gem 'enum_help'
gem 'bugsnag'
gem 'responders'
gem 'validates_timeliness'

source 'https://rails-assets.org' do
  gem 'rails-assets-babel-polyfill'
  gem 'rails-assets-es6-promise'
  gem 'rails-assets-chartjs'
  gem 'rails-assets-domurl'
  gem 'rails-assets-bs-datetimepicker'
  gem 'rails-assets-multi-select'
  gem 'rails-assets-jquery-param'
  gem 'rails-assets-axios'
  gem 'rails-assets-clipboard'
  gem 'rails-assets-bowser'
  gem 'rails-assets-bulma'
end
```

create project/config/initializers/oj.rb
```rb
Oj.optimize_rails
MultiJson.use :oj
```

install
```sh
gem install bundler --conservative
bundle install
rake db:create
rails g rspec:install
rails g migration enable_uuid_ossp
rails g migration enable_unaccent
rails g paper_trail:install
rails g devise:install
rails g action_authorizer:install
rails g devise user
rails g devise:i18n:views
erb2slim -d app/views/
rails g devise:i18n:locale en
rails g responders:install
rails g validates_timeliness:install
rails g bugsnag API_KEY
```
