# data-liberation-template

This repository is the **working Python template** copied by [`scripts/scaffold.py`](https://github.com/brianckeegan/data-liberation-skill/blob/main/scripts/scaffold.py) in the [data-liberation skill](https://github.com/brianckeegan/data-liberation-skill) when scaffolding a new civic-data liberation project.

## Normal use

You shouldn't need to clone this repo directly. Instead, from a clone of the skill:

```bash
python scripts/scaffold.py \
  --dest ~/code/your-project \
  --name your-project \
  --description "What your project liberates" \
  --author "You <you@example.org>" \
  --owner your-github-username
```

`scaffold.py` will fetch this template (pinned to a tagged release), copy it into your destination, and substitute the `{{ project_name }}`, `{{ project_slug }}`, `{{ description }}`, `{{ author }}`, `{{ owner }}`, and `{{ consumer_stack }}` placeholders.

## What's in here

A working scaffold: pipeline CLI, pandera-validated schema, optional concept catalog, idempotent fetcher, Datasette publishing module, Quarto site, opt-in GitHub Actions for refresh / publish / gh-pages.

A freshly rendered project passes `ruff check` and `ruff format --check` out of the box, which is what the included `tests.yml` workflow runs.

For the conventions this template implements, see the skill's [`references/project-template.md`](https://github.com/brianckeegan/data-liberation-skill/blob/main/references/project-template.md).

## Versioning

Tagged in lockstep with the skill — `v0.1.0` of this repo pairs with `v0.1.0` of the skill. `scaffold.py` defaults to a known-good tag; users can override with `--template-version`.

## Hacking on the template directly

If you're editing the template itself (not scaffolding from it):

```bash
git clone https://github.com/brianckeegan/data-liberation-template.git
cd data-liberation-template
# The Jinja-style {{ placeholders }} make Python files unparseable in places
# (e.g., pyproject.toml's [project.scripts] table). To test changes, render
# into a temp directory with scaffold.py and lint/test there:
python /path/to/data-liberation-skill/scripts/scaffold.py \
  --dest /tmp/test --name test --description "Test" \
  --author "You <you@example.org>" --owner you \
  --template-repo .
```

## License

MIT — see [`LICENSE`](LICENSE).
