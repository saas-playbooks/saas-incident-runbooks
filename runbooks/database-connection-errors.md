# Database Connection Errors

> Database Connection Errors

**Severity:** High — data layer unavailable  
**Full playbook:** [Database Connection Errors](https://saasplaybooks.dev/playbook/database-connection-errors)

## Symptoms

- `could not connect` / `too many connections` / timeouts.
- Intermittent failures under load.

## Likely causes

1. Connection pool exhausted.
2. Wrong host/port/credentials in prod.
3. DB max-connections too low for the number of workers.
4. Network/firewall or DB restarted.

## Immediate triage

- [ ] Confirm the DB is up and reachable from the app host.
- [ ] Check current vs max connections.
- [ ] Verify the connection string in production.

## Diagnosis

- `psql` from the app host to test connectivity.
- Inspect `pg_stat_activity` for idle/leaked connections.
- Check pool size × worker count vs DB max_connections.

## Resolution

- Right-size the pool, or add a pooler (PgBouncer).
- Fix credentials/host and restart.
- Kill leaked idle-in-transaction sessions.

## Prevention

- Use a connection pooler in production.
- Alert on connection saturation before it hits the ceiling.

## Related

- 📖 Full step-by-step playbook: [Database Connection Errors](https://saasplaybooks.dev/playbook/database-connection-errors)
- 🔴 [All incident runbooks](../README.md)

---

<sub>Part of <a href="https://saasplaybooks.dev">SaaS Builder Playbooks</a> — 70 step-by-step playbooks for building, shipping, and running a SaaS. Maintained by <a href="https://github.com/saas-playbooks">@saas-playbooks</a>.</sub>
