# Cody CMS

A JavaScript Content Management System built on Node.js

We're excited to announce that Cody CMS has successfully completed its transition to Express 4!

## Features

* Node.js-based CMS platform
* Intuitive graphical interface with WYSIWYG editor enabling non-technical users to manage content, users, files, forms, and images
* Tree-structured GUI with drag-and-drop functionality for organizing site structure and editable content using templates
* Seamless integration with your existing Node.js code

## Getting Started

Follow these steps to set up your CMS quickly. If you encounter any issues, please report them on our GitHub repository and we'll address them promptly.

### Installation

1. Install [Node.js](http://nodejs.org/download/) and [MySQL](http://dev.mysql.com/downloads/mysql/)

2. Create and navigate to a new directory for your CMS:
   ```bash
   $ mkdir jscms
   $ cd jscms
   ```

3. Install Cody and its dependencies:
   ```bash
   $ npm install cody
   ```

4. Set up a new website using the guided scaffolding:
   ```bash
   $ node ./node_modules/cody/bin/create_site
   
   Creating cody web tree in current directory
   1) Enter sitename: mysite
   Note: also using my site as database name.
   Note: by default the mysql root user has no password so you can just hit enter, if you forgot the root password see http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html
   2) Enter root password for mysql so we can create a new database and user: 
   3) Enter site database user: mysitename
   4) Enter site database password: mysitepassword
   5) Enter hostname for site: mysite.local (or localhost)
   Site mysite has been prepared.
   
   Please create DNS entries, or add to /etc/hosts:
   127.0.0.1     mysite.local
   
   Also check index.js and config.json to fine-tune extra parameters, encryption key, ...
   
   Start your site using:
   forever start mysite.js
   or
   node mysite.js
   ```

5. Add a DNS entry for the specified hostname:
   ```bash
   $ sudo bash -c 'echo 127.0.0.1 mysite.local >> /etc/hosts'
   ```

6. Start the server:
   ```bash
   $ node mysite.js
   ```
   Or use Forever to automatically restart the server on changes:
   ```bash
   $ forever start mysite.js
   ```

7. Access your site:
   - Main site: `http://mysite.local:3001`
   - CMS dashboard: `http://mysite.local:3001/en/dashboard`
   
   Default users: `super`, `admin`, `test`, `user` (password: `empty` for all)
   
   You can also use `http://localhost:3001` as an alternative.

## Configuration

The `create_site` scaffolding generates a `config.json` file in your project root. You can modify the configuration in three ways (listed in order of precedence—later methods override earlier ones):

1. **Manual editing**: Adjust values directly in the `config.json` file
2. **Custom config file**: Create your own configuration and supply it via the `-c` option (available since v3.2.5)
   ```bash
   $ node index.js -c my_overwriting_config.json
   ```
3. **Environment variables**: Set variables directly in the command line
   ```bash
   $ dbuser=dbuser dbpassword=dbpassword port=8080 node index.js
   ```

**Note**: Configuration changes require a server restart to take effect. Refer to the generated `config.json` file for available configuration options.

## Troubleshooting

##### Error: "ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2)" during scaffolding
> MySQL server is not running.
- **Mac OS**: Go to "System Preferences" → "MySQL" → "Start"
- **Unix**: Run `$ mysqld &`

##### Password prompt appears after "5) Enter hostname for site"
> Incorrect MySQL root password entered.
- Retrieve or reset your MySQL root password: http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html

## License

This project is licensed under the MIT License. See the LICENSE.md file for details.