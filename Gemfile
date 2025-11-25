source "https://rubygems.org"

# Jekyll
gem "jekyll", "~> 4.3"

# Tema
gem "minima", "~> 2.5"

# Plugins
group :jekyll_plugins do
  gem "jekyll-relative-links"
  gem "jekyll-optional-front-matter"
  gem "jekyll-readme-index"
  gem "jekyll-titles-from-headings"
end

# Windows y JRuby no incluyen archivos de zona horaria, así que los agregamos
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end

# Performance-booster para watching en Windows
gem "wdm", "~> 0.1", :platforms => [:mingw, :x64_mingw, :mswin]

# Lock `http_parser.rb` gem to `v0.6.x` on JRuby builds
gem "http_parser.rb", "~> 0.6.0", :platforms => [:jruby]

# Mermaid support (via JavaScript, no gem needed)
