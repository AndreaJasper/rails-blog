# Rails Blog

## Technology and Stack
See `Gemfile` for version numbers unless otherwise indicated.

<!-- - [PostgreSQL 11.5](https://www.postgresql.org/docs/current/static/release-11-5.html) -->
- [Ruby 2.6](https://www.ruby-lang.org) (see [.ruby-version](./.ruby-version))
- [Rails 6.1.0](https://guides.rubyonrails.org/v6.1/)
- [SQLite3](https://www.sqlite.org/download.html)
- [Node.js](https://nodejs.org/en/download/)
- [Yarn](https://classic.yarnpkg.com/en/docs/install/#windows-stable)
<!-- - [Node 10.15](https://nodejs.org/) (see `.nvmrc`)
- [sass](http://sass-lang.com/documentation/file.SASS_REFERENCE.html)
- [UIKit 3](https://getuikit.com/docs) css framework
- [Uploadcare](https://uploadcare.com/docs) file uploads (Note: we forked this and `to_s` is now the same as `cdn_url_with_operations`)
- [CKEditor5](./vendor/ckeditor5/README.md)
- [RABL](https://github.com/nesquena/rabl) -->

## Testing
- [rspec](http://rspec.info/documentation/)
- [capybara](https://github.com/teamcapybara/capybara)
<!-- - [factory_bot_rails](https://github.com/thoughtbot/factory_bot_rails)
- [faker](https://github.com/stympy/faker)
- [guard](https://github.com/guard/guard) -->

## Setup
Before installing Rails, check to make sure that your system has the proper prerequisites installed:
1. `ruby --version`
1. `sqlite3 --version`
1. `yarn --version`
1. `gem install rails`
1. `rails --version`
<!-- 1. `nvm use` - make sure you're using the correct version of Node
1. `bundle install` - Install dependencies
1. `npm install`
1. `npm run ckeditorinstall`
1. `npm run ckeditorbuild`
1. `cp config/application.yml.example config/application.yml` - Edit local config as necessary.
1. `cp config/database.yml.example config/database.yml` - Edit to match your database configuration.
1. `bundle exec rails db:setup` - Run the setup script (or `bundle exec ./bin/setup`).
1. `bundle exec rails db:migrate` - Run database migrations. -->

Run the development server and test suite to verify successful deployment.

## Development Server
- `bundle exec rails server`
- View site at `http://localhost:3000/`
- To run Sidekiq and workers - `bundle exec sidekiq`

## Testing
- `bundle exec rspec spec` or `bundle exec guard` (runs the server and watches the tests)

### Testing Policy Specs
- A helper function, `user_context`, was created to provide a session for users.
- For examples of how to use `user_context`, see `spec/policies/hapyning_policy_spec`.

**Gotchas:**
- Testing that a rails error was raised (i.e. `ActiveRecord::RecordNotFound`) cannot be done with a javascript (`:js`) test. [more info](https://stackoverflow.com/questions/18260482/activerecordrecordnotfound-for-record-just-created-in-js-true-feature-spec)
- If you are having issues with certain styles / assets not compiling properly (visual inconsistencies) run -
`bundle exec rake tmp:cache:clear` and  `bundle exec rake assets:precompile`

## Development Process
- See [PROCESS](PROCESS.md)
- Follow this [style guide](https://github.com/bbatsov/ruby-style-guide) with the exceptions noted in `.rubocop.yml`
  - To see rubocop errors, in your terminal run `rubocop`

## Project No-Nos
- Do not add self-closing divs because jQuery cannot correctly update the DOM when these are used. This was initially noticed as a bug when moving between steps in the create new hapyning modal.

## Pull Request Notes
- Heroku automatically creates review apps from PR's. There will be a link in the PR to "View Deployment" or you can find all review apps by visiting the [pipeline on Heroku](https://dashboard.heroku.com/pipelines/49346467-12e7-4351-b9f4-7cc38bb0c024)
- These review apps are seeded, so you can check the seeds file for users to log in as.
- **Gotchas:** If you are testing links in emails, you will have to edit the url manually. When you click the link in the email it will use the staging url, you'll need to replace that with the url for the specific review app you are testing.
