# 960

[Fischer random chess](https://en.wikipedia.org/wiki/Fischer_random_chess) (Chess960) randomizer web app based on my [fischer960](https://github.com/joakim/fischer960) library.

To quickly get a random starting position for your games (or tournaments), just go to:
https://960.fly.dev/

Features:
- Slick, suspenseful animation
- The ID of the starting position is shown below the board ([0-indexed](https://en.wikipedia.org/wiki/Fischer_random_chess_numbering_scheme))
- To randomize again, hit the R key or the button in the bottom right corner
- To skip the suspenseful animation, hit the Space key or click the board
- Save to home screen to use as an app on smart phones
- It should be accessible, also for screen readers (let me know if it's not!)

Built with [SvelteKit](https://kit.svelte.dev/), using [svelte-canvas](https://github.com/dnass/svelte-canvas) to render the 2D chessboard. Deployed to [Fly.io](https://fly.io/).

This was hacked together while watching Fischer Random World Championship 2022, so the code base is a little messy. I couldn't get SvelteKit to run on Fly.io, so it just builds a static page for now. Otherwise it would accept URLs like https://960.fly.dev/518. PRs are welcome!


## License

This is free and unencumbered software released into the public domain. See [full license](/LICENSE).

[Chess piece images](https://commons.wikimedia.org/wiki/Category:SVG_chess_pieces) by Cburnett are licensed under the [Creative Commons Attribution-Share Alike 3.0 Unported](https://creativecommons.org/licenses/by-sa/3.0/deed.en) license.

[Refresh icon](https://commons.wikimedia.org/wiki/File:Ic_refresh_36px.svg) by Google Inc. is licensed under the [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/deed.en) license.

