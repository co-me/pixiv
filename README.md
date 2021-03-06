# Pixiv gem

A client library for [pixiv](http://www.pixiv.net/)

[![Build Status](https://secure.travis-ci.org/uasi/pixiv.png?branch=master)][travis]
[![Dependency Status](https://gemnasium.com/uasi/pixiv.png?travis)][gemnasium]
[![Code Climate](https://codeclimate.com/badge.png)][codeclimate]

[travis]: http://travis-ci.org/uasi/pixiv
[gemnasium]: https://gemnasium.com/uasi/pixiv
[codeclimate]: https://codeclimate.com/github/uasi/pixiv

## Important Note

The pixiv Guidelines [[en][Guidelines.en], [ja][Guidelines.ja]] prohibit to
crawl the pixiv service. Do not abuse this library or you may be banned!

[Guidelines.en]: http://www.pixiv.net/guideline.php?lang=en
[Guidelines.ja]: http://www.pixiv.net/guideline.php?lang=ja

## Installation

Add this line to your application's Gemfile:

    gem 'pixiv'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install pixiv

## Synopsis

```ruby

pixiv = Pixiv.client('pixiv_id', 'password') {|agent|
  agent.user_agent_alias = 'Mac Safari'
}

illust_id = 123
illust = pixiv.illust(illust_id)
if illust.manga?
  pixiv.download_manga(illust, ['manga/', :image_name])
else
  pixiv.download_illust(illust, ['illust/', :image_name])
end

member_id = 456
member = pixiv.member(member_id)
member.works.each do |illust|
  puts illust.title
  puts illust.caption
end

me = pixiv.member
me.bookmarks.each do |illust|
  author = illust.member
  puts author.name
  puts author.works.count
end

```

## Usage

See [a sample script](https://gist.github.com/4362297)

## Documentation

[Documentation for uasi/pixiv on rubydoc.info](http://rubydoc.info/github/uasi/pixiv/master/frames)

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
