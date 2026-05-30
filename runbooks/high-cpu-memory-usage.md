# High CPU / Memory Usage

> High CPU / Memory Usage

**Severity:** Medium/High — degraded or OOM-killed  
**Full playbook:** [High CPU / Memory Usage](https://saasplaybooks.dev/playbook/high-cpu-memory-usage)

## Symptoms

- Server slow; latency climbing.
- Process OOM-killed and restarted.
- CPU pinned at 100%.

## Likely causes

1. Memory leak / unbounded in-memory cache.
2. N+1 queries or a hot unindexed query.
3. Too many workers for the box.
4. Large payloads processed in-memory.

## Immediate triage

- [ ] `top`/`htop` — which process and how much?
- [ ] Correlate the spike with a deploy or traffic change.
- [ ] Check slow-query and request logs.

## Diagnosis

- Profile memory growth over time.
- Find the slow/expensive endpoint or query.
- Compare worker count to available CPU/RAM.

## Resolution

- Add the missing index / fix the N+1.
- Cap worker count and per-worker memory; recycle workers periodically.
- Stream large payloads instead of buffering.

## Prevention

- Set resource alerts before saturation.
- Recycle workers after N requests to bound leaks.
- Load-test before launch.

## Related

- 📖 Full step-by-step playbook: [High CPU / Memory Usage](https://saasplaybooks.dev/playbook/high-cpu-memory-usage)
- 🔴 [All incident runbooks](../README.md)

---

<sub>Part of <a href="https://saasplaybooks.dev">SaaS Builder Playbooks</a> — 70 step-by-step playbooks for building, shipping, and running a SaaS. Maintained by <a href="https://github.com/saas-playbooks">@saas-playbooks</a>.</sub>
