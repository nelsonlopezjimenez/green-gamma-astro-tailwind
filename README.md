
# green-gamma-astro-tailwind

## 10.20.2024

1. Rebase by Flavio Copes
1. add file commit -am 'm1'
1. add second file commit -am 'm2'
1. git checkout -b feature
1. create file commit -am 'f1'
1. second file commit -am 'f2'
1. git checkout main
1. create file git commit -am 'm3'
1. create second file git commit -am 'm4'
1. git log -all --oneline --graph
1. git rebase feature onto main
1. if something wrong do git reset --hard ORIG_HEAD
1. I did git reset --merge ORIG_HEAD
1. It went back but it messed the merge by mixing the f1 and f2 into secondmain
when i should've been only m1m2m3m4
1. Now it looks correct: output is m1m2m3m4f1 and text.txt is m1m2m3m4f1f2
1. f2 was not a problem because it was done after m4, which I still do not understand.
1. The question is: merge or rebase?
1. Flavio's answer: ***first rebase the branch you want to merge on the branch you want to merge into, then merge***
1. on the command line:
```sh 
git checkout feature
git rebase main
open text.txt file to solve the conflict
put f1 after m3m4
save the file
git add test.txt
git rebase --continue
in commit message type f1 as that is the commit that generated the conflict
if something goes wrong
git reset --hard ORIG_HEAD
to restore the pre-rebase state
restart the rebase from scratch
```
1. When you rebase your feature based on latest main, you are moving the base of your feature to the end of main branch. Feaure's commits are reapplied to the end of main commits one by one.
1. switch to main and do merge to feature (that was rebased) this is ***fast-forward merge***. This is because the commits in main are already rebased in feature branch, so Git update the HEAD of main to point to the commit that feature branch is on, just move a pointer keeping the clean history, of course if the repo has not been pushed yet to github. 
1. In case when the history has changed in github, this to do rebase is risky.
1. Because feature's history appears as direct continuation of main history, no need to mark the new commit as ***merge commit***.
1. The benefit: **linear history**
1. Rebase rewrites the history. So only for changes that have not been pushed or shared with others yet. 


## 10.18.2024

1. Create private key
1. git config --global uaser.name and user.email are at ~/.gitconfig
1. ssh-keygen -t ed25519 -C "local1905@canva.ed"
1. selected default values
1. id_ed25519 changed to id_25519-local1905
1. Edit ~/.ssh/config file
```
Host github.com
   User nelsonlopezjimenez
   IdentityFile ~/.ssh/id_ed25519-local1905
```
1. login into github with nelson.lopezjimenez@seattlecolleges.edu and password Dineroux2 ar rorboa oldd add ressth
1. 2 factor auth using my phone
1. cloned astro-tailwindcss-verdaccio
1. npm install with verdaccio 5.11 
1. 



## 10.18.2024

1. Too hard to refactor astro-tailwindcss-verdaccio already in github.
1. npm create astro@latest
1. selected blog
1. Pending add tailwind
1. npx astro add tailwind
1. Selected defaults




# Astro Starter Kit: Blog

```sh
npm create astro@latest -- --template blog
```

[![Open in StackBlitz](https://developer.stackblitz.com/img/open_in_stackblitz.svg)](https://stackblitz.com/github/withastro/astro/tree/latest/examples/blog)
[![Open with CodeSandbox](https://assets.codesandbox.io/github/button-edit-lime.svg)](https://codesandbox.io/p/sandbox/github/withastro/astro/tree/latest/examples/blog)
[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/withastro/astro?devcontainer_path=.devcontainer/blog/devcontainer.json)

> 🧑‍🚀 **Seasoned astronaut?** Delete this file. Have fun!

![blog](https://github.com/withastro/astro/assets/2244813/ff10799f-a816-4703-b967-c78997e8323d)

Features:

- ✅ Minimal styling (make it your own!)
- ✅ 100/100 Lighthouse performance
- ✅ SEO-friendly with canonical URLs and OpenGraph data
- ✅ Sitemap support
- ✅ RSS Feed support
- ✅ Markdown & MDX support

## 🚀 Project Structure

Inside of your Astro project, you'll see the following folders and files:

```text
├── public/
├── src/
│   ├── components/
│   ├── content/
│   ├── layouts/
│   └── pages/
├── astro.config.mjs
├── README.md
├── package.json
└── tsconfig.json
```

Astro looks for `.astro` or `.md` files in the `src/pages/` directory. Each page is exposed as a route based on its file name.

There's nothing special about `src/components/`, but that's where we like to put any Astro/React/Vue/Svelte/Preact components.

The `src/content/` directory contains "collections" of related Markdown and MDX documents. Use `getCollection()` to retrieve posts from `src/content/blog/`, and type-check your frontmatter using an optional schema. See [Astro's Content Collections docs](https://docs.astro.build/en/guides/content-collections/) to learn more.

Any static assets, like images, can be placed in the `public/` directory.

## 🧞 Commands

All commands are run from the root of the project, from a terminal:

| Command                   | Action                                           |
| :------------------------ | :----------------------------------------------- |
| `npm install`             | Installs dependencies                            |
| `npm run dev`             | Starts local dev server at `localhost:4321`      |
| `npm run build`           | Build your production site to `./dist/`          |
| `npm run preview`         | Preview your build locally, before deploying     |
| `npm run astro ...`       | Run CLI commands like `astro add`, `astro check` |
| `npm run astro -- --help` | Get help using the Astro CLI                     |

## 👀 Want to learn more?

Check out [our documentation](https://docs.astro.build) or jump into our [Discord server](https://astro.build/chat).

## Credit

This theme is based off of the lovely [Bear Blog](https://github.com/HermanMartinus/bearblog/).
