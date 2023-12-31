# 1. Setting up authentication keys

## 1.1. Generate a new SSH key

```bash
ssh-keygen -t ed25519 -C your+github+address@users.noreply.github.com
```

* `Enter file in which to save the key` - If you have no other keys in the SSH directory, then the default option is fine. Otherwise, just copy the whole default path and append something to the end.
* `Enter passphrase` - The default option (empty for no passphrase) is fine.

## 1.2. Add public key to GitHub

* Go to [SSH key settings](https://github.com/settings/keys) on GitHub.
* Click `New SSH key` button.
* `Title` - A descriptive label for the new key.
* `Key type` - Select `Authentication Key`.
* `Key` - Paste everything here from the generated `.pub` file (found in the SSH directory).

After following all these steps, you should be able to clone repositories using SSH.

<br>

---
# 2. Setting up commit signing

## 2.1. Generate a new SSH key

Same as above.

## 2.2. Add public key to GitHub

Almost the same as above.  
Select `Signing Key` as a `Key type`.

## 2.3. Configure Git

```bash
git config --global gpg.format ssh
```
```bash
git config --global user.signingkey PATH/TO/.pub/FILE
```
```bash
git config --global commit.gpgsign true
```

After following all these steps, the commits from now on should be labeled verified on GitHub.

<br>

---
# 3. Transfer keys

## 3.1. Copy keys

Copy your SSH key files into the .ssh directory of your new system.  
($HOME/.ssh)

## 3.2. Add keys

Open PowerShell as administrator and run these commands:

```bash
Get-Service ssh-agent | Set-Service -StartupType Automatic
```

```bash
Start-Service ssh-agent
```

```bash
ssh-add PATH/TO/PRIVATE/KEY/FILE
```
