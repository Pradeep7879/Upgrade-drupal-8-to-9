# Upgrade-drupal-8-to-9
Some useful commands and step to follow and get success.

Step 1:- install the required module.

    composer require 'drupal/upgrade_status:^3.9'
It show the all custom/contrib module to update into drupal 9

    composer require 'drupal/hacked:^2.0@beta'
It tracked the files of core, contrib and custom. to changes anything happened.

Step 2:-  Update one by one contrib and custom module according to Drupal 9 and check in upgrade status.

1.  On every module to update, after you run either the update.php or drush updb.
2.  If any depricated changes and remove for drupal 9 in custom module, create the patch.
3.  Patch is always mention in composer.json file.
4.  after all done to check upgrade_status there is no remaining for drupal 9 update module.
5.  Then run the command:-
    
        composer remove drupal-composer/drupal-scaffold --no-update
        
6.  then add in composer.json file below line:-
     
        composer require drupal/core-composer-scaffold:^8.8 --no-update
        
7.  And then configure it by editing your composer.json file to include the necessary configuration in the **"extra"** section:

            "extra": {
          "drupal-scaffold": {
              "locations": {
                  "web-root": "web/"
              }
          },
        }
        
8.  Replace in sites/default/settings.php file:-

    From   
    
            $config_directories['sync']
    To
           
            $settings['config_sync_directory']
             
9.  Now, delete the (vendor, composer.lock, core, module/contrib).
10.  Run the composer install on terminal   

**Thanks you are upgrading from Drupal 8 to Drupal 9**


#

**Upgrade-drupal-8-minor-to-major-version**

1.  Goto **Available update** check the recommended version and update.
2.  On every module to update, after you run either the update.php or drush updb.
3.  Patch is always mention in composer.json file.
4.  Now update the core using run command on terminal.
          
        composer require drupal/core-recommended:8.9.17 --update-with-all-dependencies
