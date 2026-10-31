# How to decrypt

You need the passphrase (a file called `repo-key.txt`; it is NOT in this
repository — the owner gives it to reviewers out-of-band).

```sh
# decrypt (enter the passphrase when prompted, or use --passphrase-file FILE)
gpg -d ensemble-engine-20261031.tar.zst.gpg > ensemble-engine.tar.zst
# verify the archive is intact (compare to the hash in README.md)
sha256sum ensemble-engine-20261031.tar.zst.gpg
# unpack into a new directory -> the repo at HEAD, .git history included
mkdir ensemble-engine && tar -I zstd -xf ensemble-engine.tar.zst -C ensemble-engine
cd ensemble-engine && git log --oneline && git status --porcelain
```

If `gpg` is unavailable: `zstd` + any OpenPGP tool with the same passphrase.
