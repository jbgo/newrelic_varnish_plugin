## New Relic Varnish Extension

### Instructions for running the Varnish extension agent

1. Clone this repo: `git clone https://github.com/jbgo/newrelic_varnish_plugin.git`
2. `cd newrelic_varnish_plugin`
3. `bundle`
4. `cp config/template_newrelic_plugin.yml config/newrelic_plugin.yml`
5. Edit `config/newrelic_plugin.yml` and replace "YOUR_LICENSE_KEY_HERE" with your New Relic license key
7. Install the plugin with `rake newrelic_plugin:install`
8. Start the service with `sudo start newrelic_varnish_plugin`
9. Verify it's running by checking the logs `tail -f log/monitor-1.log`
10. Wait a few minutes and check your varnish plugin dashboard in New Relic.

### Monitoring multiple varnish instances

If you are running multiple varnish instances and would like to see them separetely in new relic,
complete the following steps before starting the plugin.

1. Edit `/etc/varnish/default` and add `-n name` to the `DAEMON_OPTS` setting. Be sure that the option
  goes inside the quotes and that you escape with a `\` if you put it on its own line.
2. Restart varnish: `sudo service varnish restart`
3. Update the `vname` setting in `config/newrelic_plugin.yml` to match your `-n` option.
3. Start (or restart) the newrelic_varnish_plugin
