user_management
===============

Role for managing users on hosts.

Requirements
------------

None

Role Variables
--------------
`default_home`: Default path for home (/home/*name*)

`user_state`: Temporary var for the user state (defaults to present)

`users_{host,group,all}`: Array with users

    users_{host,group,all}:
      - name: foo (required)
        uid: 1000 (required)
        comment: any comment you want (optional)
        password: Hash of the password (optional, defaults to '!')
        shell: /usr/bin/bash (optinal, defaults to /usr/bin/zsh)
        home: /home/foo2 (optional, defaults to /home/{name})
        remove: no (optional, defaults to yes)
        state: present (optional, defaults to present)
        authorized_keys:
        - key: (optional)
          state: present (optional, defaults to present)
        groups:
        - .. (optional, these groups will be appened to the users groups.
              When a group does not exist on a host, it will be skipped.)

Dependencies
------------

None

Example Playbook
----------------

`some_host_vars.yml`:

    users_group
      - name: foo
        uid: 1001
        groups:
        - sudo
        - audio
        - fuse

`some_playbook.yml`:

    - hosts: managed_users
      sudo: yes
      roles:
      - user_management

License
-------

The MIT License (MIT)

Copyright (c) 2014 Julian Stiller

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

Contributing
------------

I welcome contributed improvements and bug fixes via the usual github
workflow:

1. Fork this repository
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new pull request
