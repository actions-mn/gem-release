[![test](https://github.com/actions-mn/gem-release/actions/workflows/test.yml/badge.svg)](https://github.com/actions-mn/setup-flavors/actions/workflows/test.yml)

# gem-release

Setup extra flavors that aren't come with default `metanorma` installation, like this

```yml
...
- run: gem build some.gemspec

- uses: actions-mn/gem-release@main
  with:
    api-key: ${{ secrets.RUBYGEMS_API_KEY }}
```

Or

```yml
...
- uses: actions-mn/gem-release@main
  with:
    api-key: ${{ secrets.RUBYGEMS_API_KEY }}
    release-command: |
      gem build *.gemspec
      gem push *.gem
```

Or

```yml
- uses: actions-mn/gem-release@main
  with:
    github-pakages-token: ${{ secrets.PAT_TOKEN }}
    release-command: |
      bundle exec rake build
      gem push --key github --host https://rubygems.pkg.github.com/metanorma pkg/*.gem
```

> NOTE: this action only works for metanorma from ruby-gems

> NOTE: if `metanorma-cli` installed with `bundle install` make sure to path `use-bundler: true` to the action