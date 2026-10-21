<p align="center">
  <img src="images/URANIA.png" alt="URANIA" width="256">
</p>

<p align="center">
  <i><b>U</b>nita <b>R</b>erum <b>A</b>utomatio <b>N</b>avigatione <b>I</b>ntelligentiae <b>A</b>rtificialis</i>
</p>

[Urania](https://en.wikipedia.org/wiki/Urania) is the Muse of Astronomy and Geometry.
This project takes its name from _Urania_, and I call upon Her to bring me inspiration.

## Concept

Our brain is constantly receiving information and reacting to it. Suddenly an idea appears and you take note soon before it vanishes. All these notes then become something you and other people collaborate to create.

Basically the local folder with notes is synced across devices. Humans and AI agents can use it as a knowledge base for the things are being created which are in other folders, for example git repositories.

Imagine you taking notes on your tablet and AI sending you a URL to try out your new idea.

## Implementation

Ok, that was the main idea. Let's put it in practice with a concrete implementation example.

For instance if the sync method chosen is an S3 bucket, then humans can use [Obsidian](https://obsidian.md/) app with the [Remotely Save](https://community.obsidian.md/plugins/remotely-save) plugin and agents use [Rclone](https://rclone.org/) CLI.

### Initialization

Steps to do only once.

#### On your AWS account

Create an S3 Bucket on AWS.

Create an AWS user, for instance `urania-sync` with IAM permissions to read/write the bucket.

#### On your computer

Store the Bucket name in an environment variable: `URANIA_S3_BUCKET`.

Create an `URANIA` AWS CLI profile:

```sh
aws configure --profile URANIA
```

Create an URANIA folder for the Obsidian vault and fill it with the bucket content

```
mkdir URANIA
cd URANIA
aws s3 sync s3://$URANIA_S3_BUCKET . --profile URANIA
```

With Obsidian, open a vault and point to the new URANIA folder.

Open Obsidian _Settings > Community plugins_ and _Allow community plugins_ by clicking _Exit Restricted mode_.
Then search _Remotely Save_ plugin and install it. Once enabled go back to settings and configure it, add:

- Endpoint: `s3.AWS_REGION.amazonaws.com` where AWS_REGION is the region where you created the bucket.
- Region
- Access Key ID
- Secret Access Key
- Bucket Name

Other values are the same as the AWS CLI `URANIA` profile created above.

Try it out in the plugin settings, there is a _Check_ button.
