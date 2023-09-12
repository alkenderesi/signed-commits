# signed-commits
Testing how to sign commits

## Setting up authentication keys

#### 1. Generate a new SSH key

```
ssh-keygen -t ed25519 -C your+github+address@users.noreply.github.com
```

* `Enter file in which to save the key` - If you have no other keys in the SSH directory, then the default option is fine. Otherwise, just copy the whole default path and append something to the end.
* `Enter passphrase` - The default option (empty for no passphrase) is fine.

#### 2. Add public key to GitHub

* Go to [SSH key settings](https://github.com/settings/keys) on GitHub.
* Click `New SSH key` button.
* `Title` - A descriptive label for the new key.
* `Key type` - Select `Authentication Key`.
* `Key` - Paste everything here from the generated `.pub` file (found in the SSH directory).

\
After following all these steps, you should be able to clone repositories using SSH.


## Setting up commit signing

#### 1. Generate a new SSH key

Same as above.

#### 2. Add public key to GitHub

Almost the same as above. Select `Signing Key` as a `Key type`.

#### 3. Configure Git

```
git config --global gpg.format ssh
```
```
git config --global user.signingkey PATH/TO/.pub/FILE
```
```
git config --global commit.gpgsign true
```

\
After following all these steps, the commits from now on should be labeled verified on GitHub.
