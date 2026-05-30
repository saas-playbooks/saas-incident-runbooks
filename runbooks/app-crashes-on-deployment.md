# App Crashes on Deployment

> App Crashes on Deployment

**Severity:** High — new release is unusable  
**Full playbook:** [App Crashes on Deployment](https://saasplaybooks.dev/playbook/app-crashes-on-deployment)

## Symptoms

- App works locally but exits immediately in production.
- Service flaps (starts, crashes, restarts) right after deploy.

## Likely causes

1. Missing environment variable or secret in production.
2. Unpinned/uninstalled dependency.
3. Pending database migration not applied.
4. Hard-coded localhost path or dev-only config.

## Immediate triage

- [ ] Read the crash traceback: `journalctl -u <app> -n 100 --no-pager`
- [ ] Diff prod env vars against `.env.example`.
- [ ] Confirm dependencies installed in the deploy environment.

## Diagnosis

- Run the app in the foreground on the server to see the full error.
- Check the migration state matches the code.
- Verify the Python/Node version matches local.

## Resolution

- Set the missing config and restart.
- Pin and install the missing dependency, then redeploy.
- Apply migrations as part of the release step.

## Prevention

- Validate required env vars on boot and fail fast with a clear message.
- Lock dependencies (`requirements.txt`/lockfile) and build identically in CI.
- Run migrations automatically in the deploy pipeline.

## Related

- 📖 Full step-by-step playbook: [App Crashes on Deployment](https://saasplaybooks.dev/playbook/app-crashes-on-deployment)
- 🔴 [All incident runbooks](../README.md)

---

<sub>Part of <a href="https://saasplaybooks.dev">SaaS Builder Playbooks</a> — 70 step-by-step playbooks for building, shipping, and running a SaaS. Maintained by <a href="https://github.com/saas-playbooks">@saas-playbooks</a>.</sub>
