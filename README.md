# Gitterdun
Yet another GitHub secret scanner.

## Overview
Gitterdun is designed to be simple, consistent, and robust. It uses a two-pronged approach for finding secrets in GitHub:
1. Bulk clone all repos for a GitHub user or org - also works for GH Enterprise instances.
2. Concurrently pilfer any number of local repos.

## Installation
Gitterdun will work out of the box, but it is recommended to add a symlink to your `$PATH` so that you can run it from anywhere:

    sudo ln -s /path/to/gitterdun.sh /usr/local/bin/gitterdun

## Usage
You will need a Personal Access Token from GitHub to use Gitterdun. Go [here](https://github.com/settings/tokens) to get one.

Gitterdun is best suited for cases where the user already has a collection of repos suspected to contain secrets. It is **not** designed to scour GitHub for interesting repos based on a query. In fact, the only web traffic sent by Gitterdun is the initial bulk cloning. All analysis for secrets occurs offline.

Gitterdun produces output in the form of CSV files which are great for importing into Excel for analysis. However while importing, there are some default options that need to change.
1. Leave the first page on the defaults, making sure your data is **Delimited** as opposed to **Fixed width**.
2. On the second page:
    * Remove Space as a delimiter.
    * Set the delimiter to a pipe using the **Other** checkbox.
    * Change the **Text qualifier** to {none}.

[pic of importing wizard]

## Examples
**To clone all repositories for a GitHub user:**

	gitterdun -u UserName

**To clone all repositories for a GitHub organization:**

	gitterdun -o OrgName

**To scan specific local repositories:**

	gitterdun path/to/repo1 path/to/repo2 path/to/repo3 [...]

**Or, if you have all the repositories you wish to scan already in a single folder:**

	gitterdun path/to/folder/containing/repos/*

## Acknowledgements

Author:
* Austin Dean

Contributors:
* Gabe Siftar
* Dan Herlihy
