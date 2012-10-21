Heroku buildpack: SSH Keygen
=============================

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpack) which generates ssh key and places it in `$BUILD_DIR/.ssh`

Usage
-----

Example usage:

    $ ls -R *
    .ssh
    ...

    $ heroku create --stack cedar --buildpack https://github.com/abhishekmunie/heroku-buildpack-ssh-keygen.git
    ...

    $ git push heroku master
    ...
    -----> Heroku receiving push
    -----> Fetching custom buildpack... cloning with git...done
    -----> SSH-KEYGEN app detected
    -----> 
    ...

The buildpack will detect your app as SSH-KEYGEN if it has the file `.ssh` directory in the `root`.

Hacking
-------

To modify this buildpack, fork it on Github. Push up changes to your fork, then
create a test app with `--buildpack <your-github-url>` and push to it.

This buildpack runs `ssh-keygen -t rsa -q -f $BUILD_DIR/.ssh/id_rsa -N ""` to generate ssh key.