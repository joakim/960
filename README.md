# 960

Fischer random chess starting position randomizer based on my [fischer960](https://github.com/joakim/fischer960) library.

This was hacked together relatively quickly and the code base has not been cleaned up. I couldn't get SvelteKit to run on Fly.io, so it just builds a static SPA for now. But it was made to run with Node.js and accept URLs like https://960.fly.dev/518. PRs are welcome!

Built with [SvelteKit](https://kit.svelte.dev/), using [svelte-canvas](https://github.com/dnass/svelte-canvas) to render a 2D chessboard.

Deployed to [Fly.io](https://fly.io/) to get this nifty URL: https://960.fly.dev/


### [License](/LICENSE)

This is free and unencumbered software released into the public domain.

Chess piece images are licensed under the [Creative Commons Attribution-Share Alike 3.0 Unported](https://en.wikipedia.org/wiki/en:Creative_Commons) license by [Cburnett](https://commons.wikimedia.org/wiki/Category:SVG_chess_pieces).
