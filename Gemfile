# frozen_string_literal: true

source "https://rubygems.org"

gemspec

# 아래 코드를 주석처리 해제하고, 원하는 버전을 4.3.3 대신 작성한 뒤
# `bundle update jekyll` 명령어를 통해 jekyll 버전을 명시적으로 업데이트할 수 있음.
# gem "jekyll", "4.3.3"

group :test do
  gem "html-proofer", "~> 4.4"
end

# Windows and JRuby does not include zoneinfo files, so bundle the tzinfo-data gem
# and associated library.
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end

# Performance-booster for watching directories on Windows
gem "wdm", "~> 0.1.1", :platforms => [:mingw, :x64_mingw, :mswin]

# Lock `http_parser.rb` gem to `v0.6.x` on JRuby builds since newer versions of the gem
# do not have a Java counterpart.
gem "http_parser.rb", "~> 0.6.0", :platforms => [:jruby]