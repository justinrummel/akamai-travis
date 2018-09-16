# akamai-travis
Testing Travis-CI commands for Akamai DevOps

Be sure to use `travis` CLI on your local machine to encrypte your `.edgerc` file with the necessary credentials.

Example:

``` bash
admin@macbook ~/GIT/akamai-travis> travis encrypt-file _data/edgerc.txt
Detected repository as justinrummel/akamai-travis, is this correct? |yes|
encrypting _data/edgerc.txt for justinrummel/akamai-travis
storing result as edgerc.txt.enc
storing secure env variables for decryption

Please add the following to your build script (before_install stage in your .travis.yml, for instance):

    openssl aes-256-cbc -K $encrypted_47d2d923bf7d_key -iv $encrypted_47d2d923bf7d_iv -in edgerc.txt.enc -out _data/edgerc.txt -d

Pro Tip: You can add it automatically by running with --add.

Make sure to add edgerc.txt.enc to the git repository.
Make sure not to add _data/edgerc.txt to the git repository.
Commit all changes to your .travis.yml.
admin@macbook ~/GIT/akamai-travis>
```
