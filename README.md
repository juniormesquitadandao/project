# New Project

## Project
```sh
mkdir project
echo 'gem: --no-rdoc --no-ri' >> project/.gemrc
echo ruby-2.6.2 > project/.ruby-version
echo 5.2.3 > project/.ruby-gemset
\curl https://www.gitignore.io/api/rails > project/.gitignore
cd project
rvm install ruby-2.6.2
cd ../project
gem install rails --version=5.2.3
rails new . --database=postgresql --skip-git --skip-test --skip-system-test --skip-coffee --skip-bundle
```
