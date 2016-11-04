require 'bundler'
Bundler.require(:default)

# baseurl = "amarburg/site"
port = 4001

desc 'Serve pages as on the webhost'
task :serve do
    args = %w( jekyll server --incremental )
    args << %W( --port #{port})

  sh args.join(' ')
#  sh "jekyll serve -d _site/#{baseurl} -b /#{baseurl} --incremental"
end

desc 'Serve all pages (future and drafts)'
task :serve_all do
  sh "jekyll serve --incremental --drafts --future"
#  sh "jekyll serve -d _site/#{baseurl} -b /#{baseurl} --incremental --drafts --future"
end

desc 'Manually rebuild the site'
task :rebuild do
  sh "jekyll build --future"
end

desc 'Rebuild website and check with HTMLProofer'
task :check => :rebuild do
  Bundler.require(:test)

  HTMLProofer.check_directory( "./_site" ).run
end

desc 'Push website to host'
task :push do
  sh "git push origin"
end

task :publish => [:check, :push ]
