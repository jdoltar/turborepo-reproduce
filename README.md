This repo showcases a bug in turborepo, here is how to see the bug in action:

> The `dev` task is meant to simulate running a local web server, it never finishes running unless user exits.

1. `yarn install`
2. `yarn build`
3. Observe build tasks running in parallel
4. `yarn dev`
5. Observe dev tasks running in parallel.
6. `yarn dev-package-a`
7. Observe relevant dev tasks NOT running in parallel (they should be)


I a forced to define the relationship using the `devDependencies` like so: [turborepo-reproduce/compare/main...workaround](https://github.com/jdoltar/turborepo-reproduce/compare/main...workaround)
 This is not ideal because then the build tasks will depend on each other as well. I could execute with the `--parallel` flag but that wouldn't work if there were actual build-time dependencies in the mix.
