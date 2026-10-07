# Contributing

Part of [OwlGuild](https://github.com/OwlGuild).

## Ground rules

- Small pull requests; one concern per commit.
- English commit messages in the imperative mood ("Add readiness probe").
- Behaviour changes ship with a test that fails before the fix.
- CI must be green before review.

## Local checks

```bash
pip install -r requirements.txt
python manage.py check
python manage.py check --deploy
pytest -q
```

## Review

Both maintainers review before merge. Keep discussion in the PR, keep scope in the diff.
