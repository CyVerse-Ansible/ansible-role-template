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
Fill out role-readme.md, which will become readme.md.

Replace "Role Name" on line 1 with the name of your role, matching the name of your git repository but dropping the "ansible-" prefix, e.g. "purpose-of-role".

In order for the badges to work, you'll need to replace their image and link URLs.

Fill out any needed variables in a table, similar to how Ansible's core modules are documented ([example](http://docs.ansible.com/ansible/copy_module.html)).

Also, fill out meta/main.yml. What you enter here will be populated on Ansible Galaxy.

### Clean up
- Delete any empty/unused boilerplate folders and YAML files.
- Search the entire role for "role-template" and ensure you have changed its name everywhere.
- Delete this file (readme.md) and rename role-readme.md to readme.md.

### Publish

#### Configure GitHub
Create a new Git repo in [CyVerse-Ansible](https://github.com/cyverse-ansible). `git init` the role locally, commit, and push to GitHub.

#### Configure Travis CI
If you do not have one already, create a [Travis CI](https://travis-ci.org/) account and follow their instructions to link your GitHub account. Browse to your profile page and enable the new repository in Travis CI. View and copy your Travis Token from the same page, you'll need it in a minute.

#### Configure Galaxy
If you do not have one already, create an [Ansible Galaxy](https://galaxy.ansible.com/) account linked to your GitHub account.

Go to "My Roles" and click the refresh button, your new role repository should appear. Turn on the switch, click the gear, and enter your Travis Token.

#### Trigger a build + import
Any subsequent commits that you push to your GitHub repo should automatically trigger a build in Travis CI, and import the role into Galaxy once the build completes.

If you want to run an import manually, browse to [my imports](https://galaxy.ansible.com/imports) on Galaxy. The import process has built-in YAML linting, and if there are any issues preventing a successful import then you will see an error message here.
