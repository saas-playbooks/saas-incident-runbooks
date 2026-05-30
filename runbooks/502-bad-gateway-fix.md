# 502 Bad Gateway

> 502 Bad Gateway Fix Guide

**Severity:** High — site is down for users  
**Full playbook:** [502 Bad Gateway Fix Guide](https://saasplaybooks.dev/playbook/502-bad-gateway-fix)

## Symptoms

- Nginx returns `502 Bad Gateway` for all or some routes.
- Site loads static assets but app routes fail.
- Errors spike immediately after a deploy or restart.

## Likely causes

1. App server (Gunicorn/Uvicorn) crashed or never started.
2. Nginx `proxy_pass` points to the wrong socket/port.
3. App is slow to boot and Nginx times out.
4. Permissions issue on the Unix socket.

## Immediate triage

- [ ] Check the app service is running: `systemctl status <app>`
- [ ] Check Nginx error log: `tail -n 50 /var/log/nginx/error.log`
- [ ] Confirm the upstream socket/port matches Nginx config.

## Diagnosis

- `curl --unix-socket /run/app.sock http://localhost/` — does the app respond directly?
- `journalctl -u <app> -n 100 --no-pager` — look for a boot traceback.
- `ss -ltnp | grep <port>` — is anything listening?

## Resolution

- Fix the underlying app crash (see logs), then `systemctl restart <app>`.
- Correct `proxy_pass` to the right socket/port and `nginx -t && systemctl reload nginx`.
- Increase `proxy_read_timeout` if the app is simply slow to start.

## Prevention

- Add a health-check endpoint and wire it into your deploy.
- Use `systemd` with `Restart=on-failure`.
- Roll deploys with zero-downtime so a bad boot never takes the socket down.

## Related

- 📖 Full step-by-step playbook: [502 Bad Gateway Fix Guide](https://saasplaybooks.dev/playbook/502-bad-gateway-fix)
- 🔴 [All incident runbooks](../README.md)

---

<sub>Part of <a href="https://saasplaybooks.dev">SaaS Builder Playbooks</a> — 70 step-by-step playbooks for building, shipping, and running a SaaS. Maintained by <a href="https://github.com/saas-playbooks">@saas-playbooks</a>.</sub>
