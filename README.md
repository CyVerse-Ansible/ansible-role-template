This template standardizes and expedites the process of publishing easily consumed, automatically tested Ansible roles.

It extends the scaffolding provided by `ansible-galaxy init` to include the following:
- Multi-distro testing on Travis CI (currently supports CentOS 6+ and Ubuntu 12.04+)
- CyVerse documentation conventions (e.g. variables table)
- CyVerse license file

## Instructions for use
These instructions are based on https://galaxy.ansible.com/intro#create-role and http://docs.ansible.com/ansible/galaxy.html; you don't need to read those but they are good references.

Also, you don't need to use `ansible-galaxy init` if you are using this template.

### Name your role
Naming convention is "ansible-purpose-of-role" in the [cyverse-ansible](https://github.com/cyverse-ansible) Github organization.

### Copy the boilerplate
Clone this repo locally, rename the folder according to your role, and delete the .git folder (it will become a new repository).

### Build your role
Build the role functionality into the folder structure, or migrate an existing role into it.

### Write some tests
Populate section 3 of .travis.yml with tests which confirm that your role produces the desired effect on a target system. This is not strictly necessary but is strongly encouraged.

### Write the docs
Fill out role-README.md, which will become README.md.

Replace "Role Name" on line 1 with the name of your role, matching the name of your git repository but dropping the "ansible-" prefix, e.g. "purpose-of-role".

In order for the badges to work, you'll need to replace their image and link URLs.

Fill out any needed variables in a table, similar to how Ansible's core modules are documented ([example](http://docs.ansible.com/ansible/copy_module.html)).

Also, fill out meta/main.yml. What you enter here will be populated on Ansible Galaxy.

### Clean up
- Delete any empty/unused boilerplate folders and YAML files.
- Search the entire role for "role-template" and ensure you have changed its name everywhere.
- Delete this file (readme.md) and rename role-README.md to README.md. (Ansible Galaxy requires the filename to be uppercase.)

### Publish

#### Configure GitHub
Create a new Git repo in [CyVerse-Ansible](https://github.com/cyverse-ansible). `git init` the role locally, commit, and push to GitHub. Don't forget to add the `.travis.yml` dotfile, which `git add *` doesn't include automatically.

#### Configure Travis CI
If you do not have one already, create a [Travis CI](https://travis-ci.org/) account and follow their instructions to link your GitHub account. Browse to your profile page, click the "sync" button, and enable the new repository in Travis CI.

#### Configure Galaxy
If you do not have one already, create an [Ansible Galaxy](https://galaxy.ansible.com/) account linked to your GitHub account.

Go to "My Roles" and click the refresh button, your new role repository should appear. Turn on the switch.

#### Version your role
Consumers of this role will want to pin their dependency on this role to a specific version. `ansible-galaxy` uses git tags to allow users to specify a version. See http://docs.ansible.com/ansible/latest/galaxy.html#installing-multiple-roles-from-a-file. Please use the [SemVer](https://semver.org) protocol.

#### Trigger a build + import
Any subsequent commits that you push to your GitHub repo should automatically trigger a build in Travis CI, and import the role into Galaxy when a build completes *with passing status*.

If you want to run an import manually, browse to [my imports](https://galaxy.ansible.com/imports) on Galaxy. The import process has built-in YAML linting, and if there are any issues preventing a successful import then you will see an error message here.

## References
* http://www.jeffgeerling.com/blog/testing-ansible-roles-travis-ci-github
  * This tutorial was a large influence on the structure and design of this template.
