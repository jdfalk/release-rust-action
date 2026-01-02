<!-- file: TODO.md -->
<!-- version: 1.1.1 -->
<!-- guid: 12345678-1234-1234-1234-123456789001 -->

# TODO - release-rust-action

## CI/CD Failures - HIGH PRIORITY

### ✅ Fix Cargo.toml Missing Error - COMPLETED

**Status:** Complete **Priority:** High **Completed:** 2025-12-19

**Issue:** CI failing because cargo publish requires clean workspace **Error
Message:**

```text
Error: The process '/home/runner/.cargo/bin/cargo' failed with exit code 101
```

**Root Cause:**

- cargo publish requires a clean workspace by default
- Format checks and other operations modify files before publish
- Need to allow dirty workspace for publish step

**Fix Applied:**

- Added `--allow-dirty` flag to cargo publish command in action.yml

**Files Updated:**

- `action.yml` - Added --allow-dirty flag to cargo publish command

**Log File:**
`../ghcommon/logs/ci-failures/release-rust-action_20251218_231443.log`

---

## Migration Tasks

### #todo Migrate to Reusable Workflows

**Status:** Pending **Priority:** Medium **Dependencies:** CI failures must be
fixed first

**Description:** After fixing CI issues, migrate this action's workflow to use
the new centralized reusable workflows from ghcommon:

- `.github/workflows/reusable-action-ci.yml`
- `.github/workflows/reusable-release.yml`

**Tasks:**

1. Fix CI failures (see above)
2. Update workflow to call reusable workflow
3. Test that workflows still work correctly
4. Pull logs and verify success
5. Document any issues encountered

---

## Testing Requirements

### #todo Comprehensive Testing

**Status:** Pending **Priority:** High

**Required Tests:**

1. Create sample Rust project for testing
2. Test action with various Rust project configurations
3. Test cross-compilation scenarios
4. Test binary upload to releases
5. Test with different target platforms

**Test Coverage:**

- [ ] Basic Rust binary build
- [ ] Cross-platform builds (Linux, macOS, Windows)
- [ ] Different Rust versions
- [ ] Cargo workspace projects
- [ ] Release artifact upload

---

## Documentation Updates

### #todo Update Action Documentation

**Status:** Pending **Priority:** Medium

**Required Updates:**

- Document CI fix in changelog
- Update README with proper usage examples
- Document testing methodology
- Add troubleshooting section

---

**Last Updated:** 2025-12-19 **Next Review:** After CI fixes complete
