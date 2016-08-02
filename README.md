# BOSH Release for fubar


## Instructions

This BOSH Release is intended to be broken in a number of ways. Its purpose is
to provide an exercise for people new to BOSH to become familiar with how
BOSH releases work, through finding errors, fixing them, and deploying dev
releases, until the application is fully functional. Keep in mind, after the [Contributing](#contributing)
section, there may be documentation in this readme that is intentionally inaccurate.

To get started with this, follow the usage instructions to generate a manifest
and start deploying this bosh release. Keep iterating through any errors encountered
until it deploys. That's not the end of it though! You will be finally done when you
can `curl http://10.244.54.2` and see the response `You win!`.

# Contributing

Since this is designed to be broken, please **DO NOT** submit pull requests/issues
regarding bugs in the release, or upload new blobs to the blobstore. That said,
we will happily welcome any PRs with the goal of helping the end-user learn more about
BOSH troubleshooting, or tweaks to help identify the bugs more quickly/accurately.

## Usage

Since this BOSH release has no final builds, you will need to create a dev build
and upload it directly to your BOSH-Lite director:

```
bosh target BOSH_HOST
git clone https://github.com/cloudfoundry-community/fubar-boshrelease.git
cd fubar-boshrelease
bosh create release --force && bosh upload release
```

## Install prerequisites

Install spruce
```
$ brew tap starkandwayne/cf
$ brew install spruce
```

Now, you can create the manifest, and attempt to deploy it.

```
templates/make_manifest warden
bosh -n deploy
```

Once deployment is successful, you'll be able to `curl http://10.244.54.2`, and receive
the output `You win!`.
