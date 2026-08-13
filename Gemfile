source "https://rubygems.org"

gem "jekyll", "~> 4.3"

# Default Jekyll plugins — safe for GitLab Pages
group :jekyll_plugins do
  # Add plugins here if you want; e.g. gem "jekyll-feed", "~> 0.17"
end

# Windows + JRuby compatibility (harmless on Linux/macOS)
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end

gem "wdm", "~> 0.1.1", :platforms => [:mingw, :x64_mingw, :mswin]

# Ruby 3.x compatibility
gem "webrick", "~> 1.8"
