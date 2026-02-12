---
layout: post
---

The Jekyll docs seem pretty bare, or at least poorly organized. I don't understand the
```
---
name: thing
---
```
format that it uses and I can't find anything that explains it. What properties are there?

...

After some googling (and being distracted by AI summaries; praise big tech) I realize it's called ["front matter"](https://jekyllrb.com/docs/front-matter). I will turn the matter inside your skull to be in front.

---

One thing that I ran into at the end was a very sneaky bug that made me learn something new: if CSS rules have the same precedence and clash between properties, the last rule takes precedence. My initial, chronological CSS additions looked like
```
.post a { text-decoration: underline; }
.post a:link { color: darkseagreen; }
.post a:visited { color: seagreen; }
.post a:hover { text-underline-offset: unset; color: teal; }
```
but after I was finished, I thought it would make more sense if `a` and `a:hover` were next to each other, so I changed it to
```
.post a { text-decoration: underline; }
.post a:hover { text-underline-offset: unset; color: teal; }
.post a:link { color: darkseagreen; }
.post a:visited { color: seagreen; }
```
thinking that nothing would have changed. Of course, I comitted the [change](https://github.com/ayilat/blog/commit/e4dd75c32eebc47f9286a2c5906689eed6210327) without enough testing and it turned out that link colors weren't changing to teal on hover. After some googling, I realized the error and switched to
```
.post a:link { color: darkseagreen; }
.post a:visited { color: seagreen; }
.post a { text-decoration: underline; }
.post a:hover { text-underline-offset: unset; color: teal; }
```

---

While I'm thinking of things to write, one problem I've come into is that GitHub won't build the site---no runners get assigned.

![GitHub workflow error message]({{ "/assets/media/2026-02-02-github-wont-build.png" | relative_url }})

Very fun. I'll try later.

---

Another CSS irregularity that I encountered was that apparently Jekyll/minima is applying a CSS property that I've never heard of (and neither has my syntax highlighter): `text-underline-offset`. Personal preference: I like to have all links underlined, so I set `text-decoration: underline` for links as you can see ↑ there. What happened was that when I hovered over links, their underline would shift down a couple pixels. It took a long time to debug since it wasn't being shown on dev tools (how???) and it still happened even when I manually disabled all properties for it.

![Three underlined links]({{ "/assets/media/2026-02-02-links-before.png" | relative_url }})
![Leftmost link's underline is lower than the rest]({{ "/assets/media/2026-02-02-links-after.png" | relative_url }})

See the 'y' occluding the line in top one but doesn't in the bottom?

---

Overall, I'm bored by this class so far since I already know web basics and Jekyll isn't very exciting to me. I haven't done anything with databases or collaborating with anyone else at all so I'm looking forward to the final project.
