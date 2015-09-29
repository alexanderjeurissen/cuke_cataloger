require 'racatt'
require 'coveralls/rake/task'


namespace 'cuke_cataloger' do

  task :clear_coverage do
    # Remove previous coverage results so that they don't get merged into the new results
    code_coverage_directory = File.join(File.dirname(__FILE__), 'coverage')
    FileUtils.remove_dir(code_coverage_directory, true) if File.exists?(code_coverage_directory)
  end


  Racatt.create_tasks

  # Redefining the task from 'racatt' in order to clear the code coverage results
  task :test_everything, [:command_options] => :clear_coverage


  # The task that CI will use
  Coveralls::RakeTask.new
  task :ci_build => [:test_everything, 'coveralls:push']
end


task :default => 'cuke_cataloger:test_everything'
