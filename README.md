# hugo
Hugo is a static website generator that builds html files from a source directory and templates.

# usage
## CLI
The CLI can be used from the docker image `docker.io/klakegg/hugo:0.111.3-ext-alpine`.
### create a local Hugo site
`podman run --rm -it -v $(pwd):/src docker.io/klakegg/hugo:0.111.3-ext-alpine new site <site-name>`
### import the Docsy theme
Copy following files/folder from https://github.com/google/docsy-example/tree/v0.7.1 into the Hugo site folder generated in previous step:
- config.toml
- go.mod
- go.sum
- content/

Set `enableGitInfo` to `false` in `config.toml` to avoid issues when deploying the Hugo server.
The `content` folder is a Docsy template that can be updated according to your site requirements.
### add content to the site
From the Hugo site directory:
`podman run --rm -it -v $(pwd):/src docker.io/klakegg/hugo:0.111.3-ext-alpine new <folder>/file.md`.  
Alternatively you can copy a file from the template in the `content` directory.
### run a local Hugo server
From the Hugo site directory:
`podman run --rm -it -v $(pwd):/src -p 1313:1313 docker.io/klakegg/hugo:0.111.3-ext-alpine server --buildDrafts`
# integration with Github
This Hugo site is deployed on Github Pages using Github actions: https://julien-sarik.github.io/hugo/
# customize the Docsy template
https://www.docsy.dev/docs/adding-content/
