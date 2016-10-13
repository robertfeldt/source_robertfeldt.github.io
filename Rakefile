require 'rubygems'
require 'rake'
require 'rdoc'
require 'date'
require 'yaml'
require 'tmpdir'
require 'jekyll'

desc "Generate blog files"
task :generate do
  Jekyll::Site.new(Jekyll.configuration({
    "source"      => ".",
    "destination" => "_site"
  })).process
end

DestGitRepo = "/Users/feldt/dev/robertfeldt.github.com"

desc "Generate and publish blog to gh-pages"
task :publish => [:generate] do
    currdir = Dir.pwd
    print(currdir)
    system "cd #{DestGitRepo}"
    system "git checkout master"
    system "mv #{currdir}/_site/* ."
    message = "Site updated at #{Time.now.utc}"
    system "git add ."
    system "git commit -am #{message.shellescape}"
    system "git push origin master --force"
    system "cd #{currdir}"
    system "rm -rf _site"
    system "echo yolo"
end

task :default => :generate