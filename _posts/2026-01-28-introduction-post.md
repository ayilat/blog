---
layout: post
---

Took me about 1.5 hours to set everything up (+30m writing this lol). I kinda laughed when Dr. Goadrich said that getting Ruby installed was going to be the hardest part since I did in approximately 5 seconds with `nix-shell -p ruby`, but getting it installed _correctly_ certainly took longer:

- The first thing was that Ruby didn't have write permission for the directory that it wanted to install gems in, so I had to change it to in my home---per this [Stack Overflow](https://stackoverflow.com/questions/75391111/how-to-solve-bundlerpermissionerror-there-was-an-error-while-trying-to-write-t) question.
- The second thing is that bundler hadn't installed a dependency which, according to (once again) [Stack Overflow](https://stackoverflow.com/questions/69890412/bundler-failed-to-load-command-jekyll), used to be included by default, so I had to manually install webrick.

Linux giveth but Linux also taketh. It would have been double as hard on Winblows thoughbeit.

***

One thing that's weird: the unchanged fork hosted on Github Pages looked identical to [Dr. Goadrich's version](https://mgoadric.github.io/minima), but when hosted locally it failed to load some stuff like the default title and header items. Now it's working fine after changing `_config.yml`, so no idea there.

***

One thing that I was confused about is how I have to manually build the site but Github Pages knows how to automatically. I guess it's looking at the `script` directory for how to, I don't know how exactly/what files it looks for when.

***

Finally, what took the longest was getting to push to the remote correctly. I don't know how it's supposed to work, but when I cloned the repo, `remote.origin.url` was set to `https://github.com/ayilat/blog` when it should have been set to `git@github.com:ayilat/blog`. So I had to go through learning the config stuff that I had forgotten from getting Git working in Lab 1 and I copied the url from it, modifying where needed---except I didn't modify where needed enough since I set the url to `git@github.com:ayilat/ayilat.github.io/blog` instead of `git@github.com:ayilat/blog`. I accidentally created a `master` branch there, so I reverted the commit, which did nothing, and then just deleted the branch through Github itself, reverting the revert. Learning experience for Git with GitHub.
