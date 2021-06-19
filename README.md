# Web-info

Installation:
  - Run server with superuser: _sudo -H -u edxapp bash_
  - Load the virtual environment for user 'edxapp': _source /edx/app/edxapp/edxapp_env_
  - Switch to the Open edX theme directory: _cd /edx/app/edxapp/edx-platform/themes_
  - Create custom theme: _mkdir my-theme_
  - Navigate to my-theme: _cd my-theme_
  - Pull theme from github repo: git init -> git remote add origin https://github.com/minhthong176881/Web-info.git -> git pull origin master
  - Open other terminal with normal user and set permission for my-theme: _sudo chmod -R 777 /edx/app/edxapp/edx-platform/themes/my-theme_
  - Config lms.yml: _nano /edx/etc/lms.yml_
    - Set "ENABLE_COMPREHENSIVE_THEMING": true
    - Set "COMPREHENSIVE_THEME_DIRS": /edx/app/edxapp/edx-platform/themes
    - Set "DEFAULT_SITE_THEME": my-theme
  - Update assets: _cd /edx/app/edxapp/edx-platform/_ -> _paver update_assets_
  - Restart edx instance: 
    - /edx/bin/supervisorctl restart lms
    - /edx/bin/supervisorctl restart edxapp_worker:
  - Open browser and go to site: _192.168.56.10_
  - Login with superuser account
  - Navigate to _192.168.56.10/admin_
  - Look for Site themes and click Add
  - Click + button in site option, add site with domain name and display name are 192.168.56.10. Save and go back to Add site theme page
  - Set Theme dir name to _my-theme_ and Save
  - Go to dashboard to see changes.
    
Usage:
  - Modify theme with the _my-theme/lms/static/sass/\_overrides.scss_
  - Apply changes: navigate to _/edx/app/edxapp/edx-platform/_ and run _paver update_assets --themes my-theme_
  
