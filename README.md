# Linux



# How Unix Permissions Work
Each file/directory has 3 sets of permissions:

- `Owner` (the user who owns it)
- `Group` (other users in the same group)
- `Others` (everyone else)

Each permission is represented as a number:
- `4` = read (`r`)
- `2` = write (`w`)
- `1` = execute (`x`)
- `0` = no permission

You add them up:
- `7` = read + write + execute (`rwx`)
- `6` = read + write (`rw-`)
- `5` = read + execute (`r-x`)
- `0` = no permissions (`---`)

Meaning of `775`
- Owner: `7` → `rwx`
- Group: `7` → `rwx`
- Others: `5` → `r-x`

So:
- `Owner`: full control
- `Group`: full control
- `Others`: can read and enter directory, but not write


### Rule of Thumb:
- `Directories` → 775 (rwxrwxr-x)
- `Socket files` → 660 (rw-rw----)

