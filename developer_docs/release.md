# Release

The following steps detail how an Ignition release is produced. This may only be performed by a user with admin rights to this Git repository and the Pypi repository.

You will need to install the following python libraries:

```
python3 -m pip install GitPython==3.1.3
python3 -m pip install twine
```

## Ensure Milestone

Ensure there is a milestone created for the release at: [https://github.com/IBM/ignition/milestones](https://github.com/IBM/ignition/milestones).

Also ensure all issues going into this release are assigned to this milestone.

## Update CHANGLOG

Update the `CHANGELOG.md` file with a list of issues fixed by this release (see other items in this file to get an idea of the desired format).

Commit and push these changes.

## Build and Release

Run the `build.py` program to perform a release:

```
python3 -m pip --release --version <THE VERSION TO BE RELEASED> --post-version <VERSION TO BE USED AFTER THE RELEASE> --pypi-user <USERNAME FOR PYPI> --pypi-pass <PASSWORD FOR PYPI USER>
```

For example:
```
python3 build.py --release --version 1.0.0 --post-version 1.0.1.dev0 --pypi-user accanto --pypi-pass mypass
```

Confirm the tags/commits were pushed to the repository origin.

## Update Release Notes

Look at previous releases to see the format. Usually, we will list the issues fixed (make sure each issue is assigned to the milestone for the release) and include links to the Pypi location of the release. This is essentially the same content you have already added to `CHANGELOG.md` so just copy and paste the entry for this release, edit the header to say `Release Notes`.

Also ensure the `-docs.tgz` file created by `build.py` is attached to the release. You should then delete this file from your machine to avoid accidentally pushing it into the repo.

## Close milestone

Close the milestone for the release in the repository at: [https://github.com/IBM/ignition/milestones](https://github.com/IBM/ignition/milestones)
