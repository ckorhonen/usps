# Repository guide

## Layout and development

This Ruby gem wraps the historical USPS WebTools API. `lib/usps/request/` constructs requests, `lib/usps/response/` parses responses, and `spec/data/` contains XML fixtures. `lib/usps/test/` contains live certification calls, separate from local specs.

Install dependencies with `bundle install` from `Gemfile` and `usps.gemspec`. The checked-in Travis matrix lists Ruby 1.9.3, 2.0, and 2.1; these are legacy compatibility evidence, not a guarantee that current dependency resolution works. Nokogiri and Typhoeus may require native build prerequisites. No lockfile or standalone lint configuration is tracked.

Run `bundle exec rake` (the default RSpec task), or `bundle exec rspec spec/path_spec.rb` for focused coverage. Specs use the `TESTING` username and XML fixtures. `bundle exec rake build` packages the gem locally. `rake certify` and loading `usps/test` send live API requests and require an authorized USPS account; they are not ordinary offline test commands. Historical API documentation does not prove current service availability.

## Completion and boundaries

Preserve the README's patch conventions: cover behavior changes, avoid unrelated Rakefile/version/history edits, and keep an explicitly requested version bump separate. Begin with `git status --short`, preserve unrelated changes, and complete authorized local work through relevant checks and repair without asking about routine reversible steps. Use synthetic addresses/tracking data and stub HTTP for unit tests.

Do not expose USPS credentials or personal address/tracking data, run live certification/label operations, or publish the gem without explicit authorization. If legacy dependencies or baseline failures block testing, report the exact failure and continue independent work. For documentation-only changes, inspect paths/commands and run `git diff --check`; close with changed paths, executed checks/results, and remaining service/runtime gaps.
