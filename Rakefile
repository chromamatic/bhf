system 'sass --update public/stylesheets/sass:public/stylesheets --style compressed'


require 'yui/compressor'
compressor = YUI::JavaScriptCompressor.new

output = ''
[
'public/javascripts/mootools-core-1.3-full-nocompat-yc.js'
].each do |js_path|

  output << File.open(js_path, 'r').read

end

[
'public/javascripts/mootools_rails_driver-0.4.1.js',
'public/javascripts/class/BrowserUpdate.js', 
'public/javascripts/class/Ajaxify.js',
'public/javascripts/bhf_application.js'
].each do |js_path|

  output << compressor.compress(File.open(js_path, "r").read)

end

# TODO: Zlib::GzipWriter.open('public/javascripts/bhf.js', 'w')
File.open('public/javascripts/bhf.js', 'w') do |file|
  file.write(output)
end



require 'rake/testtask'

Rake::TestTask.new do |test|
  test.pattern = 'test/**/*_test.rb'
  test.libs << 'test'
end


begin
  require 'jeweler'
  #exec "sass --update public/stylesheets/sass:public/stylesheets"
  
  Jeweler::Tasks.new do |gem|
    gem.name = 'bhf'
    gem.summary = 'Agnostic rails backend'
    gem.description = 'Gets you there in time'
    gem.email = 'anton.pawlik@gmail.com'
    gem.authors = ['Anton Pawlik']
    gem.files = Dir["{lib}/**/*", "{app}/**/*", "{config}/**/*", "public/stylesheets/bhf.css", "public/javascripts/bhf.js"]
    gem.homepage = 'http://github.com/antpaw/bahnhof'
    gem.rubyforge_project = 'nowarning'
    gem.add_dependency 'haml'
    
  end
  Jeweler::GemcutterTasks.new
rescue
  puts 'Jeweler or dependency not available.'
end
