[!WARNING]
**⚠️ This project has been archived and is no longer maintained. ⚠️**

Github has shown it does not respect its users. Other have said it better than I can.

- https://www.theregister.com/2022/06/30/software_freedom_conservancy_quits_github/
- https://www.andrlik.org/dispatches/migrating-from-github-motivation/
- https://techresolve.blog/2025/12/27/looking-to-migrate-company-off-github-whats-the/
- https://lord.io/leaving-github/
- https://dev.to/alanwest/how-to-actually-migrate-from-github-to-codeberg-without-losing-your-mind-33bf>
> Development has moved to Codeberg:
> **➡️ https://codeberg.org/DavidJEddy/aws-closest-region**
>
> Please update your remotes:
> ```bash
> git remote set-url origin https://codeberg.org/DavidJEddy/aws-closest-region
> ```

---
# aws-closest-region
Automatically select the closest AWS region and significantly reduce latency 🔥

[![Build Status](https://travis-ci.org/mtojek/aws-closest-region.svg?branch=master)](https://travis-ci.org/mtojek/aws-closest-region)

Status: **Done**

Find the **closest AWS region** to your customers and **reduce the latency** while accessing the service endpoint. The application can be used in both - **local development** environment and **remote production hosts**.

```aws-closest-region``` can automatically discover new launched regions!

## Live

<img src="https://github.com/mtojek/aws-closest-region/blob/master/snapshots/snapshot-1.png" alt="Screenshot Desktop" width="720px" />

## Features

 * support **100% AWS regions** in all non-gov partitions (incl. China)
 * support **100% AWS services** (also brand new ones)
 * latency measured using the HTTP protocol (*/ping* service endpoint) instead of the ICMP messages
 * **quick integration** with shell scripts (``AWS_DEFAULT_REGION=`aws-closest-region` ``)
 * automatically detect next launched endpoints (use AWS SDK models)
 * verbose mode to show all latencies

## Getting started

~~~
$ cd ~/
$ go get github.com/mtojek/aws-closest-region
$ ~/go/bin/aws-closest-region
eu-central-1
~~~

You can select also a particular service:

~~~
$ go get github.com/mtojek/aws-closest-region
$ ~/go/bin/aws-closest-region s3
INFO Service "s3" is available in 15 regions in "aws" partition. 
INFO Service "s3" is available in 2 regions in "aws-cn" partition. 
INFO Partition "us-gov" will be skipped.          
INFO Service is accessible via following endpoints: 
INFO   ap-south-1: https://s3.ap-south-1.amazonaws.com 
INFO   eu-central-1: https://s3.eu-central-1.amazonaws.com 
INFO   us-east-2: https://s3.us-east-2.amazonaws.com 
...
~~~

Or run in verbose mode:

~~~
$ go get github.com/mtojek/aws-closest-region
$ ~/go/bin/aws-closest-region --verbose s3
eu-central-1
~~~

## Verbose mode

<img src="https://github.com/mtojek/aws-closest-region/blob/master/snapshots/snapshot-2.png" alt="Screenshot Desktop" width="720px" />