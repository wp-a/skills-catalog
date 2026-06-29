# WPIRONMAN Skills Catalog

This repository is the content source for the public WPIRONMAN Skills marketplace:

https://www.wpironman.top/skills/

## How To Add A Skill

1. Add one file under `skills/<skill-id>.json`.
2. Add the file path to `manifest.json`.
3. Put the skill id into exactly one non-`all` category in `marketplace-categories.json`.
4. Optionally add it to `collections.json`, `task-briefs.json`, `stack-blueprints.json`, or `discovery-routes.json`.
5. In the blog repository, run:

```bash
npm run sync:skills-catalog
npm test
```

## Required Skill Fields

Each skill file should include:

- `id`
- `name`
- `source`
- `origin`
- `category`
- `creator`
- `workflow`
- `installType`
- `status`
- `quality`
- `description`
- `bestFor`
- `avoidWhen`
- `verification`
- `install`
- `repo`
- `tags`

The blog sync script fills dossier fields such as user role, inputs, outputs, failure modes, quick start, and trust from `defaults-by-category.json` when a skill does not define them explicitly.

## Maintenance Rule

The catalog is public, but it should stay curated. Do not add a skill unless it has a clear repository/source, a realistic use case, and at least two verification standards.
