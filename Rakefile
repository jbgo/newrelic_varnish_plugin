require 'fileutils'

namespace :newrelic_plugin do
  desc <<-DESC
Install init scripts with foreman export

Options (specify as environment variables):
  app  - the name of the app (default: newrelic_varnish_plugin)
  user - the user to run the plugin as
  log  - absolute path to the log directory
  format - foreman export output format (default: upstart)
DESC
  task :install do
    app = ENV.fetch 'app', 'newrelic_varnish_plugin'
    log = ENV.fetch 'log', File.join(File.dirname(__FILE__), 'log')
    user = ENV.fetch 'user', `whoami`.chomp
    format = ENV.fetch 'format', 'upstart'

    sudo_cmd = `which ruby` =~ %r{/\.rvm/} ? 'rvmsudo' : 'sudo'

    FileUtils.mkdir_p log

    foreman_args = "--app #{app} --user #{user} --log #{log}"
    cmd = "#{sudo_cmd} foreman export #{format} /etc/init #{foreman_args}"
    puts "running `#{cmd}`"
    `#{cmd}`

    if $?.exitstatus == 0
      puts "Success: newrelic_varnish_plugin installed"
      puts "Start it by running `sudo start newrelic_varnish_plugin`"
    else
      puts "Error: failed to install newrelic_varnish_plugin"
    end
  end
end
