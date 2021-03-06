# WordPress Accumulations Plugin

_Version 0.0.0_

### by Bain Design

# WordPress Setup

If you just want to install the plugin and display your air quality data on your website, here's what you need to do.

* Download the plugin .zip archive and unpack it. 
* Locate the plugin file and upload to your website Plugins folder.
* Log into WordPress and activate the plugin. 
* Once the plugin is activated... COMING SOON!

# Development

If you want to collaborate on this plugin or fork your own version, here's a brief guide. 

## VVV Setup

Add the following to your VVV `config.yml` 

```
  wp-accumulations:
    skip_provisioning: false
    repo: https://github.com/markbaindesign/wp-accumulations.git
    hosts:
      - wp-accumulations.test
    custom:
      delete_default_plugins: true
      install_plugins:
        - transients-manager
        - query-monitor
      wp_config_constants:
        WP_DEBUG: true
        WP_DEBUG_LOG: true
        WP_DEBUG_DISPLAY: false
        WP_DISABLE_FATAL_ERROR_HANDLER: true
```


## Testing

WP CLI is your friend. Here are some commands to make testing a breeze.

```
wp db tables --all-tables
wp db query 'SELECT * FROM wp_bd_accumulations_accumulation_data'
wp db query 'SELECT * FROM wp_bd_accumulations_accumulation_data ORDER BY id DESC LIMIT 10'
wp db query 'SELECT * FROM wp_bd_accumulations_mantra_data'
wp option get baindesign_foobot_api_settings
```

## Changes to table structure

When changing the database table, you must also:

1. Update the database version function
2. Deactivate the plugin
3. Reactivate the plugin

...in order for the changes to take effect.