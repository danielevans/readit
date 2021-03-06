## Simple api client of [readability](http://www.readability.com) [![Code Climate](https://codeclimate.com/badge.png)](https://codeclimate.com/github/29decibel/readit)

### Installation
```ruby

gem install readit
```
or in your rails gemfile

``` ruby

gem 'readit'
# or latest (recommend)
gem 'readit',:git=>'git@github.com:29decibel/readit.git'
```

### Configuration
#### Rails
config/readability.yml

``` ruby

development:
  consumer_key: some_key
  consumer_secret: some_secret
```

or in your code

``` ruby

Readit::Config.consumer_key = some_key
Readit::Config.consumer_secret = some_value
```

### API usage

#### Initialize api client
``` ruby 

@api = Readit::API.new 'access_token','access_token_secret'
```

#### User info
```ruby
# get user info
@api.me
```

#### Bookmarks
```ruby
# get all bookmarks, result will be a hash array
@api.bookmarks
# get bookmarks along with meta info :
# item_count, item_count_total, num_pages, page
bookmarks,meta = @api.bookmarks(:include_meta => true)

# add bookmark
bookmark_info = @api.bookmark(:url=>'http://some_article_url.html')
# check bookmarked infos
# bookmark_info.bookmark_id
# bookmark_info.article_id

# get bookmark by bookmark_id
@api.bookmarks :bookmark_id => some_bookmark_id

# archive a bookmark
@api.archive some_bookmark_id

# favorite a bookmark
@api.favorite some_bookmark_id

# or you can just call update_bookmark to 
# update a bookmark to favorited or archived
@api.update_bookmark bookmark_id,:favorite => 1,:archive => 0
```

#### Get Article
```ruby
# get one artile by article_id
@api.article 'article_id'

```

### At last but not least
>Contributions are welcome!

