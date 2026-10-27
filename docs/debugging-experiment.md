# Realistic debugging experiment notes

## Scenario
This project simulates a deployment workflow where a feature is added, but the environment is not fully configured. The `debug` route intentionally exposes configuration values that commonly fail in real pipelines.

## Typical failures
- `DATABASE_URL` missing in staging
- a broken release tag causing confusion between environments
- secret scanning detecting hardcoded credentials in config files
- a deployment job that is blocked because a required environment secret is absent

## Investigation checklist
1. Check the GitHub Actions logs.
2. Inspect the values returned by `/debug`.
3. Confirm the environment variables in GitHub repository settings.
4. Ensure that production secrets are configured under `Settings -> Secrets and variables -> Actions`.
5. Validate the deployed version matches the expected release tag.
