source 'https://rubygems.org'

ruby '3.4.10'

gem 'jekyll', '~> 4.4'

# Explicitly declared because _config.yml depends on them directly:
# kramdown's GFM input parser and the rouge highlighter. Jekyll pulls both in
# as transitive deps, but naming them here keeps that reliance intentional.
gem 'kramdown-parser-gfm', '~> 1.1'
gem 'rouge', '~> 4.7'

# Plugins listed in _config.yml
gem 'jekyll-sitemap', '~> 1.4'

group :development do
  gem 'bundler-audit', '~> 0.9.3'
end
