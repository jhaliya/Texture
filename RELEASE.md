# Release Process
This document describes the process for a public Texture release.

### Preparation
- Install [github_changelog_generator](https://github.com/skywinder/Github-Changelog-Generator): `sudo gem install github_changelog_generator`
- Generate a GitHub Personal Access Token to prevent running into public GitHub API rate limits: https://github.com/github-changelog-generator/github-changelog-generator#github-token

### Process
- Run `github_changelog_generator` in Texture project directory: `github_changelog_generator --token <generated personal token> TextureGroup/Texture`
- Update `spec.version` within `Texture.podspec`.
- Create a new PR with the updated `Texture.podspec` and the newly generated changelog, add `#changelog` to the PR message so the CI will not prevent merging it.
- After merging in the PR, [create a new GitHub release](https://github.com/TextureGroup/Texture/releases/new). Use the generated changelog for the new release.
- Update `future-release` within `.github_changelog_generator` to the next version.

### Problems
- Sometimes we will still run into GitHub rate limit issues although using a personal token to generate the changelog. For now there is no solution for this. The issue to track is: [Triggering Github Rate limits #656](https://github.com/github-changelog-generator/github-changelog-generator/issues/656)