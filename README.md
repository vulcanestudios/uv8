Rails Sample App on OpenShift
=========================

Quickstart rails application for openshift.

Running on OpenShift
--------------------

Create an account at http://openshift.redhat.com/

Create a rails application

    rhc app create -a railsapp -t ruby-1.8

Add mysql support to your application
    
    rhc app cartridge add -a railsapp -c mysql-5.1

Add this upstream rails quickstart repo

    cd railsapp
    git remote add upstream -m master git://github.com/openshift/rails-example.git
    git pull -s recursive -X theirs upstream master

Then push the repo upstream

    git push

That's it, you can now checkout your application at:

    http://railsapp-$yournamespace.rhcloud.com

Security Considerations
-----------------------
This repository contains configuration files with security related variables.

Since this is a shared repository, any applications derived from it will share those variables, thus reducing the security of your application.

You should follow the directions below and push your updated files to OpenShift immediately.

### Procedure

The following table lists files and variables that should be changed.

These values can be replaced by the output of `rake secret`, which generates a securely random 128 character string.

<table>
  <tr>
    <th>File</th>
    <th>Variable</th>
  </tr>
  <tr>
    <td>config/initializers/secret_token.rb</td> 
    <td>Railsapp::Application.config.secret_token</td>
  </tr>
  <tr>
    <td>config/initializers/session_store.rb</td>
    <td>Railsapp::Application.config.session_store</td>
  </tr>
</table>
