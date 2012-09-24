require 'bundler'
Bundler::GemHelper.install_tasks

require 'rspec/core'
require 'rspec/core/rake_task'

desc 'Run rspec'
RSpec::Core::RakeTask.new(:spec) do |t|
  t.rspec_opts = %w[-c -f progress -r ./spec/spec_helper.rb]
  t.pattern = 'spec/**/*_spec.rb'
  t.verbose = true
end

desc 'Run rspec with simplecov'
task :coverage do |t|
  ENV['SIMPLE_COV'] = '1'
  Rake::Task["spec"].invoke
end

require 'yard'

desc 'Generate YARD document'
YARD::Rake::YardocTask.new(:doc) do |t|
  # skip lib/fluent/**/*.rb
  t.files   = ['lib/fluentd.rb','lib/fluentd/**/*.rb']
  t.options = []
  t.options << '--debug' << '--verbose' if ENV['TRACE']
end

task :default => :spec

