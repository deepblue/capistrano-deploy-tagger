## 2.0.0 (Aug 1, 2012)

Renamed the gem to Capistrano-Deploy-Tagger. It now creates a specified tag with timestamp for each deploy, as well as a moving tag representing the latest deploy. This makes it easy to see at a glance which revisions were ever in production.

If you're migrating over from the ['capistrano-ec2-selfdeploy-tag'](https://rubygems.org/gems/capistrano-ec2-selfdeploy-tag) gem, you'll need to remove your previous configuration as property names have changed.

Features:

  - When you run a standard 'cap deploy', the 'inproduction' tag is updated to refer to the revision that was just deployed.

  - In addition, the revision is also tagged in the format 'deploy-YEARMONTHDAY-HOURMIN-SECS' which gives you a history of revisions that were deployed to production.

  - You can change the name of the moving tag from 'inproduction' by setting :latest_deploy_tag in your deploy.rb.

  - You can also prevent updating tags by setting :update_deploy_tags to false in your deploy.rb.

Fixed
 
 - Errors were being shown when initially creating the 'inproduction' tag.

## 1.0.3 (November 16, 2011)

Bugfix:

  - Suddenly started failing on a subset of servers, related to not requiring rubygems or capistrano.

## 1.0.2 (September 14, 2011)

  - Added a dummy 'deploy:first_time' task. Override this task in your project if there are commands that need to be run the first time a project deploys, but not during each subsequent deploy.

## 1.0.1 (September 13, 2011)

Bugfixes:

  - When ':update_selfdeploy_tag' is set to false, we no longer exit with a status of 1.

## 1.0.0 (June 13, 2011)

Features:

  - Running a standard 'cap deploy' will move the 'inproduction' tag to whatever commit was just deployed.
  - You can 'set :selfdeploy_tag, "your_tag_name"' to change the tag name used.
  - You can prevent the tag from being moved for specific tasks by using 'set :update_selfdeploy_tag, false'.
  - Running 'cap ec2_instance deploy' ensures the deployment takes place from the 'inproduction' tag and prevents the tag from being moved. Use this task with your autoscaling self deployments.