source "https://rubygems.org"

# Use modern Jekyll 4.x instead of github-pages (which pins to old Jekyll 3.9)
gem "jekyll", "~> 4.3.0"
gem "minima", "~> 2.5"

# Jekyll plugins
group :jekyll_plugins do
  gem "jekyll-feed", "~> 0.12"
  gem "jekyll-seo-tag"
  gem "jekyll-sitemap"
end

# Required for Ruby 3.4+ compatibility - gems moved out of standard library
gem "webrick", "~> 1.7"
gem "csv"
gem "bigdecimal"
gem "drb"
gem "mutex_m"
gem "base64"

# Windows and JRuby does not include zoneinfo files
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end

# Performance-booster for watching directories on Windows
gem "wdm", "~> 0.1.1", :platforms => [:mingw, :x64_mingw, :mswin]
