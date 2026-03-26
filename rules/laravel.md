---
paths:
  - "**/*.php"
---

# Laravel Pre-Implementation Checklist

Before writing or modifying PHP/Laravel code, work through these questions. Do not skip them.

## Existence and Duplication (DRY)

- Does this class, method, trait, or helper already exist somewhere in the codebase? Search before creating.
- Is there an existing pattern in the codebase for this type of work? Follow it.
- Am I duplicating validation rules that already exist in a Form Request?
- Am I writing a query that an existing Eloquent scope already handles?
- Am I recreating something Laravel already provides out of the box (helpers, collections methods, string methods, etc.)?
- Is there an existing event, listener, or job that already handles this concern?
- Does a policy already exist for this model?
- Am I writing a utility/helper that already exists in a shared namespace?

## Single Responsibility (SRP)

- Does this class do exactly one thing? If I need the word "and" to describe it, it should be split.
- Am I putting business logic in a controller? It should be in an action or dedicated class.
- Am I creating a service class? Service classes are reserved for wrapping 3rd party APIs/integrations only. Do not use service classes to separate or organize application logic. Use actions, jobs, or other dedicated classes instead.
- Am I putting display/formatting logic in a model? It belongs in a resource, view model, or presenter.
- Is this model getting fat? Should this behavior be extracted into a concern, trait, or action?
- Is this method doing more than one job? Each method should have one reason to change.
- Am I mixing query building with business logic? Queries belong in scopes or dedicated query classes.
- Does this middleware handle more than one concern? Split it.
- Is this job orchestrating too many steps? Break it into smaller, composable jobs or use a pipeline.

## Laravel Conventions

- Am I using `Illuminate\Database\Eloquent\Casts\Attribute` for accessors and mutators, not the legacy `getSomePropertyAttribute` / `setSomePropertyAttribute` magic methods?
- Am I using Form Request classes for validation instead of inline `$request->validate()` in controllers?
- Am I leveraging route model binding instead of manually fetching models?
- Am I using Eloquent relationships and eager loading instead of manual joins or N+1 queries?
- Am I dispatching events for side effects rather than chaining unrelated logic?
- Am I using config/env values through `config()` and never calling `env()` outside of config files?

## Before Submitting

- Can I remove any code I wrote and reuse something that already exists?
- If I added a new class, does it have a single, clear purpose?
- Would another developer understand this class's responsibility from its name alone?
