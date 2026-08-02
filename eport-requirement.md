# E-Portfolio / newmodule Requirement

This document defines the working rules for `mod_newmodule` so the plugin can be copied to another Moodle site and keep working with minimal edits.

## 1. Target Environment

- Moodle 3.10 family
- PHP 7.4.x
- MySQL-compatible database accessed with `mysqli` or Moodle `$DB`
- Apache on Windows in this deployment, but code must stay portable

## 2. Core Design Goals

- Keep the plugin copyable to any Moodle site
- Avoid hardcoded absolute paths, hostnames, and environment-specific values
- Keep the code structured, reusable, and easy for humans to maintain
- Use one clear responsibility per file
- Prefer standard Moodle output and standard Moodle page lifecycle
- Keep runtime side effects to a minimum
- Log important events without spamming logs

## 3. Portability Rules

- Use `__DIR__`, `$CFG->dirroot`, `$CFG->wwwroot`, and `moodle_url` instead of Windows paths or fixed URLs
- If a site-specific connection file is needed, keep it in one place only
- Do not spread database connection logic across many files
- Do not assume the same database name, domain, or folder structure exists on another server
- If a file is optional, the code must fail gracefully and explain what is missing
- If code needs a file from outside the plugin root, ask the user before wiring it in so they can provide the exact file from the server
- Do not invent fallback paths for external files unless the user has approved that behavior

## 4. File Structure Rules

- Keep CSS in one shared file per plugin when possible, for example `css/newmodule.css`
- Keep page-specific JS in `js/` and avoid inline script blocks unless absolutely necessary
- Keep shared UI fragments in `includes/`
- Keep reusable server-side helpers in `includes/` or `classes/`
- Avoid duplicated footer or header fragments in page files
- Do not create temporary files at runtime unless the feature explicitly needs them and the location is documented

Suggested layout:

```text
mod/newmodule/
  v_index.php
  v_*.php
  includes/
    toper.php
    selectcur.php
    dbconn.php
  css/
    newmodule.css
  js/
  img/
```

## 5. Moodle Page Rules

- Use the normal Moodle bootstrap flow
- Use `require_once(dirname(dirname(dirname(__FILE__))).'/config.php');`
- Set `$PAGE->set_url()`, `$PAGE->set_title()`, and `$PAGE->set_heading()`
- Render with `echo $OUTPUT->header();`
- Finish with `echo $OUTPUT->footer();`
- Do not use a custom footer include on pages that already use standard Moodle footer output
- Do not leave output buffering wrappers in place unless there is a clear reason
- Do not use raw `$_GET` or `$_POST` when Moodle parameter helpers can be used
- Use `optional_param()` / `required_param()` with the correct parameter type

## 6. Database Rules

- Prefer Moodle `$DB` for Moodle data
- If legacy `mysqli` access is required, isolate it in one helper file only
- Use prepared statements for every dynamic query
- Close statements and free result sets
- Do not build SQL with string concatenation for user input
- Do not create new database tables unless the change is planned and documented
- Do not write schema changes silently during page load
- If the plugin depends on an external or legacy database, keep the connection setup in one reusable file
- If a required file or asset is missing from the plugin package, stop and ask for it instead of guessing a substitute path

## 7. External DB Config Rules

- A connection helper such as `config-condata-elearning.php` must only do one job: create the connection
- It should read from `$CFG` when loaded inside Moodle
- It should fall back to safe defaults only when needed
- It must not echo debug output on success
- On failure, it should log the error and show one clear user-facing message
- It must not create tables, files, or other side effects

## 8. HTML / CSS Rules

- Use semantic HTML elements: `main`, `section`, `nav`, `table`, `thead`, `tbody`
- Avoid inline CSS
- Put responsive layout rules in the shared stylesheet
- Use wrapper classes for wide tables so mobile screens can scroll instead of breaking the layout
- Keep spacing, colors, and typography in CSS, not in PHP
- If an image or asset is missing, the page must still render cleanly
- Use a standard footer from Moodle and do not duplicate footer markup inside page content

## 9. Logging Rules

Log only things that matter for maintenance:

- missing config file
- database connection failure
- SQL prepare/execute failure
- missing expected record
- unexpected empty dataset when data should exist
- permission denied or access blocked
- missing asset that affects the page

Logging format:

- Prefix logs with the plugin name, for example `[newmodule]`
- Keep one log line short and specific
- Include the page name and the failing action
- Do not log passwords, tokens, raw session data, or full SQL dumps

Example:

```php
error_log('[newmodule][v_index] Failed to fetch curriculum list: ' . $e->getMessage());
```

## 10. Error Handling Rules

- Show a short user-friendly message
- Log the technical detail separately
- Catch specific exceptions when possible
- Do not swallow errors silently
- Do not rely on `die()` unless the page cannot continue at all
- If the page cannot render safely, stop cleanly and explain the missing dependency

## 11. Code Style Rules

- Keep functions small and focused
- Use meaningful variable names
- Add comments only where the reason is not obvious
- Remove dead code before delivery
- Remove old commented-out experiments before copying to another site
- Keep translations and business rules readable
- Use consistent indentation and brace style

## 12. Testing Rules

Before copying a change to another site, verify:

- `php -l` passes on edited PHP files
- the page returns HTTP 200
- the page opens without PHP warnings or fatal errors
- responsive layout works at desktop and mobile widths
- no broken image or CSS resource appears in the page
- the page still works after cache refresh

## 13. Minimum Acceptance Checklist

The plugin change is acceptable only if:

- it can be copied to a new Moodle site without rewriting business logic
- it uses one standard footer path
- it keeps styles in one shared CSS file
- it logs important failures
- it does not create extra DB objects unnecessarily
- it is readable and maintainable by a human after you leave it
