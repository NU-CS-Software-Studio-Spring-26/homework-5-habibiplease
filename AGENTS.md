# Agent brief — sample todo app

## Stack

Rails 8.1 sample todo app, SQLite3, Hotwire (Turbo + Stimulus via importmap), Propshaft for assets, Minitest (not RSpec) under `test/`, Solid Queue / Solid Cache / Solid Cable for background jobs and adapters. No Bootstrap; plain ERB and `application.css`.

## Commands

- Setup: `bin/setup` (bundle, `db:prepare`, optional `bin/dev`)
- Run dev: `bin/dev`
- Console: `bin/rails console`
- Tests: `bin/rails test` and `bin/rails test:system`
- Lint: `bin/rubocop`
- Security scan: `bin/brakeman`

## Conventions

- RESTful `TodosController` with HTML and JSON formats; no Devise or per-user authorization yet.
- Shared todo markup lives in `app/views/todos/_todo.html.erb`; use `dom_id(todo)` for Turbo targets.
- Strong parameters via `params.expect(todo: [...])` in the controller.
- Prefer Turbo Streams (`format.turbo_stream` + `*.turbo_stream.erb`) over custom JS for partial page updates.
- Generators: `bin/rails generate` for migrations and scaffolds; keep this app scoped to todos only.

## Don'ts

- Do not add gems without explicit approval.
- Do not use inline JavaScript in ERB; use Stimulus controllers under `app/javascript/controllers/` if JS is needed.
- Do not skip CSRF verification (`skip_before_action :verify_authenticity_token`).
- Do not seed real user credentials or PII; use `db/seeds.rb` and fixtures only.
- Do not disable mass-assignment protection or log/filter secrets from `.env` or credentials.
