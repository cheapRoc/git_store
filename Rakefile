require 'rake'
require "rdoc/task"

begin
  require 'rspec/core/rake_task'
rescue LoadError
  puts <<-EOS
To use rspec for testing you must install the rspec gem:
    gem install rspec
EOS
  exit(0)
end

desc "Run all specs"
RSpec::Core::RakeTask.new(:spec) do |t|
  t.rspec_opts = ['-cfs']
  t.pattern = 'test/**/*_spec.rb'
end

desc "Print SpecDocs"
RSpec::Core::RakeTask.new(:doc) do |t|
  t.rspec_opts = ["--format", "specdoc"]
  t.pattern = 'test/*_spec.rb'
end

desc "Generate the RDoc"
Rake::RDocTask.new do |rdoc|
  files = ["README.md", "LICENSE", "lib/**/*.rb"]
  rdoc.rdoc_files.add(files)
  rdoc.main = "README.md"
  rdoc.title = "Git Store - using Git as versioned data store in Ruby"
end

desc "Run the rspec"
task :default => :spec
