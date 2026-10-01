# hibr apt repository

Debian and Ubuntu packages of [hibr](https://github.com/osakka/hibr), a
small, fast shell that runs the bash you already write.

## Install

```text
curl -fsSL https://osakka.github.io/hibr-apt/hibr.gpg \
  | sudo tee /usr/share/keyrings/hibr.gpg > /dev/null
echo "deb [signed-by=/usr/share/keyrings/hibr.gpg] https://osakka.github.io/hibr-apt stable main" \
  | sudo tee /etc/apt/sources.list.d/hibr.list
sudo apt update
sudo apt install hibr
```

`apt upgrade` keeps it current from then on. The first line adds the key the
repository is signed with, kept apart from the system's own keys and trusted
for this repository only; the second adds the repository.

Then `hibr` runs a script, `man hibr` lists every option, and
[From bash to hibr, in ten minutes](https://github.com/osakka/hibr/blob/main/docs/tutorial.md)
is the place to start.

## What there is

| | |
|---|---|
| architectures | amd64 (arm64 to follow) |
| needs | glibc 2.34 or later: Debian 12, Ubuntu 22.04, or newer |
| installs | `/usr/bin/hibr`, modules in `/usr/lib/hibr`, `man hibr`, and the text desktop (`desktop`) |

## The signing key

```text
hibr apt repository (signs https://github.com/osakka/hibr-apt) <osakka@gmail.com>
fingerprint A1E3 CA78 8A8F B020 52DA  22B4 1303 5BE1 B167 4431
```

`hibr.gpg` is the key in the form apt reads, and `hibr.asc` the same key as
text. Check the fingerprint after downloading it:

```text
gpg --show-keys /usr/share/keyrings/hibr.gpg
```

## Removing it

```text
sudo apt remove hibr
sudo rm /etc/apt/sources.list.d/hibr.list /usr/share/keyrings/hibr.gpg
```

This repository is written by `packaging/deb/publish.sh` in the hibr source;
the packages are built by `packaging/deb/build-deb.sh`.
