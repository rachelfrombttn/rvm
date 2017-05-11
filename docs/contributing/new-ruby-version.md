# Adding support for new version of Ruby
 
Following files needs to be updated to add support for a new version of already supported Ruby interpreter.
Please follow patterns used in those files and add entries in appropriate location. 
[\#3805](https://github.com/rvm/rvm/commit/c5845cf75f030f8e881e6ab3554dee4f9cc72b46) contains good example of the required changes.

* `config/known`
  * update existing entry when minor version released 
  * add new entry when major version released
* `config/known_strings` - same rules as above
* `config/db` - update only for stable releases
* `config/md5` - add new line with `md5` hash of the interpreter source
* `config/sha512` - add new line with `sha512` hash of the interpreter source

When listing interpreter source make sure that you link to the smallest archive variant (usually `.bz2`).

When release package does not include `md5` or `sha512` hashes you should download the source package and calculate it yourself.
One of the ways to do that would be to use `openssl` command:

```
openssl dgst -sha512 FILE
openssl dgst -md5 FILE
```