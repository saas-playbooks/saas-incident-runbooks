# Static Files Not Loading

> Static Files Not Loading

**Severity:** Medium — site renders unstyled  
**Full playbook:** [Static Files Not Loading](https://saasplaybooks.dev/playbook/static-files-not-loading)

## Symptoms

- CSS/JS return 404; page loads without styling.
- Works in dev but not in production.

## Likely causes

1. `collectstatic`/build step skipped.
2. Nginx `location /static/` path is wrong.
3. File permissions block the web server.
4. Cache-busting hash mismatch.

## Immediate triage

- [ ] Open a static URL directly in the browser — 404 or 403?
- [ ] Check Nginx maps `/static/` to the correct directory.
- [ ] Confirm the build/collect step ran in the deploy.

## Diagnosis

- `ls -l` the static root the web server points at.
- Check Nginx access log for the requested path.

## Resolution

- Run the static build/collect step and reload Nginx.
- Fix the `location` block to the real path; `nginx -t && systemctl reload nginx`.
- Fix directory permissions/ownership.

## Prevention

- Make the static build a required, verified deploy step.
- Serve hashed filenames with long cache headers.

## Related

- 📖 Full step-by-step playbook: [Static Files Not Loading](https://saasplaybooks.dev/playbook/static-files-not-loading)
- 🔴 [All incident runbooks](../README.md)

---

<sub>Part of <a href="https://saasplaybooks.dev">SaaS Builder Playbooks</a> — 70 step-by-step playbooks for building, shipping, and running a SaaS. Maintained by <a href="https://github.com/saas-playbooks">@saas-playbooks</a>.</sub>
