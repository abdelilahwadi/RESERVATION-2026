# Projet Réservations completion checklist

The goal is a theatre catalogue and reservation app with a public catalogue, member booking and reviews, a role-protected back office, and an affiliate API. Follow iterations 0–10 from the PID, then verify the complete application and prepare the course submission. Check off a task when its expected behavior has been verified.

## Current state

- [x] The Laravel 12 scaffold and Composer dependencies are present in the repository root.
- [x] The local SQLite database contains the three default Laravel migrations.
- [ ] Run the application and its tests. The current shell could not find `php` during the code review.
- [ ] Create the first Git commit. Local `main` had no commits at the time of review.

**Resume at Iteration 1.** Finish local verification and the Git hand-in, then build the artist list and detail pages in Iteration 2. Run application commands from the repository root. The `application` subfolder is empty.

## Iteration 0 — Project discovery

- [ ] Review the PID's use cases, database diagram, and mockups. Compare a few theatre booking sites for their catalogue, booking, and navigation flows.
- [ ] Record the actions and permissions for visitors, members, administrators, affiliates, press critics, and producers.
- [ ] Map the legacy XML sample to artists, artist functions, shows, venues, and performances. Complete the data dictionary as the remaining tables are designed.
- [ ] Agree on open business rules with the group. Record booking quantity and availability rules, cancellation behavior if in scope, eligibility to review a show, affiliate-tier permissions, and what should happen to existing bookings when catalogue records change.
- [ ] Record which group-specific features are in scope. Use the PID's business model as context when discussing payment or merchandise.

## Iteration 1 — Framework setup and first hand-in

- [ ] Make PHP and Composer available in the project terminal and check their versions. Verify Node.js and npm for the frontend assets.
- [ ] Verify local environment settings, the application key, the database connection, and migration status. Keep machine-specific secrets in the ignored `.env` file.
- [ ] Install frontend dependencies and build the assets. Start Laravel, open `/` and `/up`, and run `php artisan test`.
- [ ] Set up the group's project board and add the first tasks. Document how to run the app locally.
- [ ] Commit the scaffold and project files, push to the course repository, and submit the repository link as instructed.

## Iteration 2 — Artist list and detail

- [ ] Create the `Artist` model and the `artists` migration. Use `firstname` and `lastname`, each with the PID's 60-character limit, and seed sample artists.
- [ ] Implement artist list and detail routes, controller actions, and Blade templates. Add navigation from the list to a detail page and back.
- [ ] Verify the populated list, the empty state, an existing artist, and a missing artist ID. Push the iteration to the course repository.

## Iteration 3 — Simple CRUD and validation

- [ ] Add artist create, edit, and delete actions, forms, and routes. Show validation errors and preserve submitted field values when validation fails.
- [ ] Create and seed the standalone `types` table for artist functions. Implement the standalone CRUD required by the course before linking types to artists.
- [ ] Verify successful writes, invalid input, missing records, and CSRF protection. Apply the role restrictions in Iteration 4 before exposing write actions to visitors.
- [ ] Push the iteration to the course repository.

## Iteration 4 — Authentication and roles

- [ ] Adapt the starter kit's authentication approach to Laravel 12. Implement registration, login, logout, password reset, and profile editing.
- [ ] Implement the PID registration fields and defaults, including login, name, email, language, and the `member` role. Verify password hashing and the registration confirmation flow.
- [ ] Define role checks for administrator, affiliate, press critic, and producer actions. Enforce permissions on the server and limit producer actions to their own shows.
- [ ] Protect catalogue write routes and back-office pages. Verify guest access, member access, administrator access, and attempts to modify another user's records.
- [ ] Push the iteration to the course repository.

## Iteration 5 — Relational data and core workflows

- [ ] Add models, migrations, constraints, and seed data for localities, venues, shows, performances, prices, reservations, and reviews. Complete the role and membership relationships.
- [ ] Map artists to functions and shows through `artist_type` and `artist_type_show`. Map shows to prices, performances to reservations, and users to roles. A show can have multiple performances, and a performance can take place at a different venue from the show's creation venue.
- [ ] Implement related-record pages and forms. Show linked records on detail pages, allow authorized users to attach or detach existing records and create related records, and define deletion behavior for dependent records.
- [ ] Build the member reservation flow. Let a member choose a performance, ticket quantity, and eligible price, then view their own reservations. Validate availability at write time and make booking changes atomic so concurrent requests cannot overbook a limited performance.
- [ ] Build reviews for members who attended a show, article or link submission for press critics, and sales statistics and moderation for producers of the relevant shows.
- [ ] Verify relationships, booking and pricing rules, authorization, and representative edge cases. Push the iteration to the course repository.

## Iteration 6 — Publish the affiliate API

- [ ] Expose the agreed catalogue data through API routes and JSON resources. Use the artist API roadmap as the worked example.
- [ ] Implement Sanctum token issuance and revocation. Enforce the agreed Free, Starter, and Premium permissions on the server.
- [ ] Add pagination and navigation links where applicable. Document authentication, endpoints, sample responses, and error behavior.
- [ ] Verify authorized requests, missing and invalid tokens, revoked tokens, and access denied by tier. Push the iteration to the course repository.

## Iteration 7 — Integrate a third-party component

- [ ] Choose and integrate a third-party package for a PID feature such as back-office CRUD, CSV import/export, RSS, or the API. Record the package and what it delivers.
- [ ] Complete the secure admin catalogue workflow, including manual editing and batch actions. Add CSV import with validation and clear error reporting, then add export.
- [ ] Publish the RSS feed for upcoming performances. Verify each feature and document any setup it requires.

## Iteration 8 — Implement the screens and navigation

- [ ] Translate the PID mockups into responsive Blade layouts for the public catalogue, registration, login, and authenticated navigation. Include the member and administrator screens needed by the completed workflows.
- [ ] Build the public catalogue with a title sort by default and 10 shows per page. Add keyword search, sorting by title, venue, reservability, and price, and filters for venue and reservability. Preserve those choices across pages.
- [ ] Show each production's venue, contributors, upcoming performances, prices, and booking availability in its detail view.
- [ ] Match the PID's registration flow with asynchronous field feedback and server-side validation. Verify keyboard access, mobile layouts, empty results, error states, and role-specific navigation.

## Iteration 9 — Consume a third-party API

- [ ] Select a public or Open Data theatre source based on its available catalogue data and access requirements.
- [ ] Map external shows, venues, and performances to local records. Keep source identifiers so re-importing can update records without duplicating them.
- [ ] Give an authorized administrator a way to trigger or review a catalogue update. Handle provider errors and partial data without losing existing catalogue records.
- [ ] Test a successful import, a repeat import, and a failed provider request. Document configuration and the fields that are synchronized.

## Iteration 10 — Cookie controls

- [ ] Implement the PID's cookie banner and settings flow. Inventory the cookies or tracking included in the finished app and document how preferences affect them.
- [ ] Verify first-visit behavior, saving a choice, changing it later, and continued access to essential application workflows.

## Final verification and submission

- [ ] Run a fresh setup from the README, apply migrations and seed data, build the frontend, and run the test suite.
- [ ] Walk through the main scenarios as a visitor, member, administrator, affiliate, press critic, and producer. Include a complete reservation, a forbidden action, a CSV import, an RSS response, and both API directions.
- [ ] Review validation, role checks, secret handling, and query behavior on catalogue pages. Verify that example configuration and test data contain no real credentials.
- [ ] Update the README with setup, demo data, roles, and integration configuration. Finish the written report with the data model, implementation decisions, and evidence for the PID criteria.
- [ ] Push the final revision and verify that the submitted repository can be accessed. Submit the required deliverables and prepare the oral defense around the main workflows.

## References

- `PID-ProjetReservations.docx` — Functional brief, iterations, data model, and assessment criteria.
- `Support-de-cours-de-projet.html` — How the course uses the roadmaps, labs, and debriefs.
- `Roadmap-PHP_Laravel11.docx` — Starter kit for local setup, artist CRUD, and authentication. Adapt the Laravel 11 examples to the project's Laravel 12 setup.
- `Roadmap-Laravel12_Mapping.docx` — Primary implementation guide for models, migrations, and Eloquent relationships. `Roadmap-Laravel11_Mapping.docx` covers the corresponding chapters for Laravel 11.
- `Roadmap-Laravel11_API.docx` — Example of an artist API, Sanctum authentication, and hypermedia links. The PID defines the affiliate product scope.
