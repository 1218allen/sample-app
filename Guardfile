# A sample Guardfile  
# More info at https://github.com/guard/guard#readme  
require 'active_support/core_ext'  
  
guard 'spork', :rspec_env => { 'RAILS_ENV' => 'test' } do  
  watch('config/application.rb')  
  watch('config/environment.rb')  
  watch(%r{^config/environments/.+\.rb$})  
  watch(%r{^config/initializers/.+\.rb$})  
  watch('Gemfile')  
  watch('Gemfile.lock')  
  watch('spec/spec_helper.rb')  
  watch('test/test_helper.rb')  
  watch('spec/support/')  
end  
  
guard 'rspec', :version => 2, :all_after_pass => false, :cli => '--drb' do   
  watch(%r{^app/controllers/(.+)_(controller)\.rb$}) do |m|  
    ["spec/routing/#{m[1]}_routing_spec.rb",  
     "spec/#{m[2]}s/#{m[1]}_#{m[2]}_spec.rb",  
     "spec/acceptance/#{m[1]}_spec.rb",  
     (m[1][/_pages/] ? "spec/requests/#{m[1]}_spec.rb" :  
                       "spec/requests/#{m[1].singularize}_pages_spec.rb")]  
  end  
  watch(%r{^app/views/(.+)/}) do |m|  
    "spec/requests/#{m[1].singularize}_pages_spec.rb"  
  end   
end  

guard 'spork', :cucumber_env => { 'RAILS_ENV' => 'test' }, :rspec_env => { 'RAILS_ENV' => 'test' } do
  watch('config/application.rb')
  watch('config/environment.rb')
  watch('config/environments/test.rb')
  watch(%r{^config/initializers/.+\.rb$})
  watch('Gemfile')
  watch('Gemfile.lock')
  watch('spec/spec_helper.rb') { :rspec }
  watch('test/test_helper.rb') { :test_unit }
  watch(%r{features/support/}) { :cucumber }
end
