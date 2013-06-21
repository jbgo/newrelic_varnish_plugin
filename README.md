## New Relic Varnish Extension

### Instructions for running the Varnish extension agent

1. Clone this repo: `git clone https://github.com/jbgo/newrelic_varnish_plugin.git`
2. `cd newrelic_varnish_plugin`
3. `bundle`
4. Copy `config/template_newrelic_plugin.yml` to `config/newrelic_plugin.yml`
5. Edit `config/newrelic_plugin.yml` and replace "YOUR_LICENSE_KEY_HERE" with your New Relic license key
6. Edit the `config/newrelic_plugin.yml` if you are running Varnish with an -n argument
7. Install the plugin with `rake newrelic_plugin:install`
8. Start the service with `sudo start newrelic_varnish_plugin`
9. Verify it's running by checking the logs `tail -f log/monitor-1.log`
10. Wait a few minutes and check your varnish plugin dashboard in New Relic.
