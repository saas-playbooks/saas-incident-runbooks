# Media Uploads Not Working

> Media Uploads Not Working

**Severity:** Medium — user uploads fail or vanish  
**Full playbook:** [Media Uploads Not Working](https://saasplaybooks.dev/playbook/media-uploads-not-working)

## Symptoms

- Uploads 500 or silently fail.
- Files upload but 404 when viewed.
- Uploads disappear after a redeploy.

## Likely causes

1. Media directory not writable by the app user.
2. Files stored on ephemeral disk wiped on deploy.
3. Upload size exceeds Nginx `client_max_body_size`.
4. Missing/incorrect S3 credentials or bucket policy.

## Immediate triage

- [ ] Reproduce with a small file, then a large file.
- [ ] Check app + Nginx logs at the moment of upload.
- [ ] Confirm where files are meant to be stored (disk vs S3).

## Diagnosis

- Check write permissions on the media path.
- Verify `client_max_body_size` is large enough.
- For S3: confirm credentials, region, and bucket policy.

## Resolution

- Fix permissions or raise the body-size limit and reload Nginx.
- Move media to durable storage (S3 or a mounted volume).

## Prevention

- Never store user media on ephemeral app disk.
- Validate file type/size on upload.

## Related

- 📖 Full step-by-step playbook: [Media Uploads Not Working](https://saasplaybooks.dev/playbook/media-uploads-not-working)
- 🔴 [All incident runbooks](../README.md)

---

<sub>Part of <a href="https://saasplaybooks.dev">SaaS Builder Playbooks</a> — 70 step-by-step playbooks for building, shipping, and running a SaaS. Maintained by <a href="https://github.com/saas-playbooks">@saas-playbooks</a>.</sub>
