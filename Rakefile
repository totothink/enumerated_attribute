#require 'rake/testtask'
require 'rdoc/task'
require 'rubygems/package_task'
require 'rake/contrib/sshpublisher'

require 'jeweler'
Jeweler::Tasks.new do |s|
  s.name = 'enumerated_attribute'
  s.summary = 'Enumerated model attributes and view helpers'
  s.description = 'Add enumerated attributes to your models and expose them in drop-down lists in your views'

  s.add_dependency('meta_programming', '>= 0.2.1')
  
  exclude_files = FileList['**/*.log']
  s.files = FileList['{examples,lib,tasks,spec}/**/*'] + %w(CHANGELOG.rdoc init.rb LICENSE Rakefile README.rdoc .gitignore) - exclude_files
  s.require_path = 'lib'
  s.has_rdoc = true
  s.test_files = Dir['spec/*_spec.rb']
  
  s.author = ['Jeff Patmon', 'Turadg Aleahmad']
  s.email = ['jpatmon@gmail.com', "turadg@aleahmad.net"]
  s.homepage = 'http://github.com/jeffp/enumerated_attribute/'
  
  s
end

Jeweler::GemcutterTasks.new  


require "rspec/core/rake_task" # RSpec 2.0

desc "Run specs"

namespace :spec do
  task :default => :all
  RSpec::Core::RakeTask.new(:object) do |t|
    t.pattern = 'spec/*_spec.rb'
    # t.libs << 'lib' << 'spec'
    t.rcov = false
    t.rspec_opts = ['--options', 'spec/spec.opts']
    #t.rcov_dir = 'coverage'
    #t.rcov_opts = ['--exclude', "kernel,load-diff-lcs\.rb,instance_exec\.rb,lib/spec.rb,lib/spec/runner.rb,^spec/*,bin/spec,examples,/gems,/Library/Ruby,\.autotest,#{ENV['GEM_HOME']}"]
  end
  desc "Run all specs"
  task :all=>[:object] 
end


desc "Generate documentation for the 'enumerated_attribute' plugin."
Rake::RDocTask.new(:rdoc) do |rdoc|
  rdoc.rdoc_dir = 'rdoc'
  # rdoc.title = spec.name
  #rdoc.template = '../rdoc_template.rb'
  rdoc.options << '--line-numbers' << '--inline-source'
  rdoc.rdoc_files.include('README.rdoc', 'CHANGELOG.rdoc', 'LICENSE', 'lib/**/*.rb')
end

Dir['tasks/**/*.rake'].each {|rake| load rake}
