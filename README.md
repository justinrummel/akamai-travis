# akamai-travis
Testing Travis-CI commands for Akamai DevOps

Be sure to use `travis` CLI on your local machine to encrypte your `.edgerc` file with the necessary credentials.

In my repo, I have a folder `_data/` ([that is ignored](https://github.com/justinrummel/akamai-travis/blob/master/.gitignore#L107)) which is where I have my Akamai API PURGE Credentials saved as a text file.  You DON'T want your API Credentials made public, so be sure to take proper precautions!  When you run the `travis` CLI, be mindful of where you are running the command and the input/output options.  I like having the `.enc` output in the root directory of the repo, which makes it easy for Travis to find and decrypt.  When you decrypt, the Akamai CLI expects the default file to be `.edgerc`, which is what I have [in my `.travis.yml` file](https://github.com/justinrummel/akamai-travis/blob/master/.travis.yml#L16) vs. the output example that is below.

#### Example Output:

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

Travis Build Results: [https://travis-ci.org/justinrummel/akamai-travis/jobs/429319392](https://travis-ci.org/justinrummel/akamai-travis/jobs/429319392)
