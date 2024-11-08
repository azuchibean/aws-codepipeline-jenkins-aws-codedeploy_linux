#!/usr/bin/env ruby

require 'rake/testtask'
require 'rubygems'
require 'rake'
require 'haml'

task default: :compile

task :compile do
  FileList.new('./src/*.html.haml').each do |filename|
    if filename =~ /([^\/]+)\.html\.haml$/
      output_filename = "./#{$1}.html"
      File.open(output_filename, 'w') do |f|
        haml_template = File.read(filename)
        engine = Haml::Engine.new(haml_template, format: :html5)
        f.write engine.render
      end
    end
  end
end


task :clean do
  FileUtils.rm_r(Dir.glob("./*.html"), force: true)
end

task :test do 
  Rake::TestTask.new do |t|
    t.test_files = FileList['test/jenkins_sample_test.rb']
  end
end
