---
title: "Rails 使用 mongoDB 和 Slim"
categories: [tech]
---

预言中的世界末日都要来了，期待的 `Ruby 2.0` 和 `Rails 4.0` 都还没发布。那我就来看看怎么集成 [mongoDB](http://www.mongodb.org/) 和 [Slim](http://slim-lang.com/) 到一个 Rails 工程。

## 安装 mongoDB 数据库
`brew install mongodb`
安装好之后，可以把 mongo 的服务设为开机启动，或者在需要的时候手动 `mongod` 开启。

## 新建 Rails 工程
`rails new projectname --skip-test-unit --skip-active-record --skip-bundle`

因为使用 mongoDB 并打算使用 [minitest](https://github.com/seattlerb/minitest) 所以会在创建工程的时候 skip 掉不必要的东西。

## 修改 Gemfile
在 Gemfile 里面添加以下几句之后执行 `bundle install`

```ruby
gem 'slim-rails'
gem 'mongoid'
group :test, :development do
  gem 'minitest-rails'
end
```

## 生成数据库配置和 minitest helper 文件

```shell
rails generate mongoid:config
rails generate mini_test:install
```

## Slim 页面
把 application.html.erb 转换成 slim 格式，可以使用 [html2slim](http://html2slim.herokuapp.com/) 或者自己手动修改。参见我改好的[版本](https://gist.github.com/4139805)

## 使用
现在就可以使用 `rails g model | controller` 等等命令了，默认生成的 view 文件都会是 slim 格式，model 都会自动 include [mongoid](https://github.com/mongoid/mongoid) 的 class。enjoy it!
