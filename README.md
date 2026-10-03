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

For instance if the sync method chosen is an S3 bucket, then humans can use [Obsidian](https://obsidian.md/) app with the _Remotely Save_ plugin and agents use [Rclone](https://rclone.org/) CLI.

### Environment variables

URANIA uses the following environment variables:

- `URANIA_DIR`: the folder where all the notes are stored locally.
- `URANIA_REMOTE`: an URI where the notes are stored remotely, for example an S3 bucket `s3://urania.example.com` or a git repo `git@github.com:user/notes.git`.

