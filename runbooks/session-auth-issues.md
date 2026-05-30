# Session / Auth Issues in Production

> Session/Auth Issues in Production

**Severity:** High — users logged out or locked out  
**Full playbook:** [Session/Auth Issues in Production](https://saasplaybooks.dev/playbook/session-auth-issues)

## Symptoms

- Users randomly logged out.
- Login works then immediately drops.
- Auth works on one node but not another.

## Likely causes

1. Session store is per-process memory behind multiple workers.
2. Cookie `Secure`/`SameSite`/domain misconfigured for HTTPS.
3. Secret key rotated/inconsistent across instances.
4. Clock skew invalidating tokens.

## Immediate triage

- [ ] Reproduce and inspect the session cookie in devtools.
- [ ] Confirm all instances share one secret key.
- [ ] Check cookie flags against your domain/HTTPS setup.

## Diagnosis

- Confirm a shared session backend (Redis/DB), not in-memory.
- Verify `SECRET_KEY` identical across nodes.
- Check server clock sync (NTP).

## Resolution

- Move sessions to a shared store.
- Set correct cookie domain + `Secure` + `SameSite`.
- Pin one secret key across all instances.

## Prevention

- Use a shared session backend from day one when running >1 worker.
- Keep secrets in one source of truth.

## Related

- 📖 Full step-by-step playbook: [Session/Auth Issues in Production](https://saasplaybooks.dev/playbook/session-auth-issues)
- 🔴 [All incident runbooks](../README.md)

---

<sub>Part of <a href="https://saasplaybooks.dev">SaaS Builder Playbooks</a> — 70 step-by-step playbooks for building, shipping, and running a SaaS. Maintained by <a href="https://github.com/saas-playbooks">@saas-playbooks</a>.</sub>
