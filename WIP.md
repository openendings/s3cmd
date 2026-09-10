# WIP notes

## remote copy testing

**Initialise:**

```bash
mkdir -p /tmp/testdir
```

**Pretest:**

```bash
rm /tmp/testdir/* ; echo foo > /tmp/testdir/foo-`date +%Y%m%d-%H%M%S`
```

**Test:**

```bash
s3cmd sync /tmp/testdir/ s3://chrche30-backup/testdir/ --recursive --delete-removed --delete-after --debug --cache-file /tmp/s3cmd-test-cache > >(tee >(ts >> /tmp/s3cmd-test.log)) 2>&1 ;
wc /tmp/s3cmd-test.log
```
