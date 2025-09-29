# Repository Guidelines

## Project Structure & Module Organization
The gem source lives under `lib/`. Use cases and flow helpers are grouped in `lib/micro/case/`, while the public entry point is `lib/u-case.rb`. Micro-level utilities under `lib/micro` should remain internal. Example scripts (`examples/`), benchmarking suites (`benchmarks/`), and comparison scenarios (`comparisons/`) demonstrate advanced usage. Tests sit in `test/`, grouped by feature and mirroring the lib layout; shared fixtures live in `test/support`. Assets such as branding live in `assets/`.

## Build, Test, and Development Commands
Run `bundle install` before hacking. Use `bundle exec rake test` (or plain `bundle exec rake`) to execute the full minitest suite. Focused runs can use `bundle exec ruby -Itest test/path/to_case_test.rb`. `bundle exec irb -ru-case` starts a console with the gem preloaded, and `bin/console` mirrors production use.

## Coding Style & Naming Conventions
Follow standard Ruby style: two-space indentation, snake_case method/file names, and descriptive class names nested under the appropriate `Micro::Case` namespace. Keep new files frozen with `# frozen_string_literal: true`. Compose flows by declaring `flow` steps rather than inheriting from flow-enabled classes. Prefer immutable objects and pure transformations; place shared helpers inside `lib/micro/cases/utils` when reuse is required.

## Testing Guidelines
Create tests beside their implementation using `_test.rb` filenames and `describe` blocks when grouping scenarios. Use fixtures from `test/support` when possible and clean up any persistent state. Exercise both success and failure branches of each use case, and watch the CodeClimate coverage badge; raise coverage when it dips. Locally, enable coverage reporting with `COVERAGE=true bundle exec rake test`.

## Commit & Pull Request Guidelines
Write imperative, capitalized commit subjects (`Add flow builder guard`). Reference issues with `#123` in the description when relevant. Before opening a PR, ensure CI passes (`bundle exec rake test`), document behavioral changes in `README.md`, and update examples if behavior shifts. PR descriptions should outline the use case touched, list manual verification steps, and include screenshots for user-facing assets.

## Security & Configuration Tips
Never hard-code credentials; rely on environment variables when adding configuration. When touching `Micro::Case::Config`, document default changes and provide migration notes in the PR.
