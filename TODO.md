<!-- file: TODO.md -->
<!-- version: 1.0.0 -->
<!-- guid: 12345678-1234-1234-1234-123456789001 -->

# TODO - release-rust-action

## CI/CD Failures - HIGH PRIORITY

### #todo Fix Cargo.toml Missing Error
**Status:** Open
**Priority:** High
**Issue:** CI failing because Swatinem/rust-cache action cannot find Cargo.toml
**Error Message:**
```
Error: The process '/home/runner/.cargo/bin/cargo' failed with exit code 101
error: could not find `Cargo.toml` in `/home/runner/work/release-rust-action/release-rust-action` or any parent directory
```

**Root Cause:**
- The rust-cache action is looking for Cargo.toml in the repository root
- This is a composite action repository (not a Rust project)
- The action should not be using rust-cache in its CI

**Fix Required:**
- Remove or conditionally skip rust-cache action in CI workflow
- Update CI workflow to properly test the action (which is a composite action, not a Rust project)
- The action itself is designed to build Rust projects in user repositories, not this repo

**Files to Fix:**
- `.github/workflows/ci.yml` - Remove rust-cache usage or make conditional
- Test workflow needs to create a sample Rust project to test against

**Log File:** `/Users/jdfalk/repos/github.com/jdfalk/ghcommon/logs/ci-failures/release-rust-action_20251218_231443.log`

---

## Migration Tasks

### #todo Migrate to Reusable Workflows
**Status:** Pending
**Priority:** Medium
**Dependencies:** CI failures must be fixed first

**Description:**
After fixing CI issues, migrate this action's workflow to use the new centralized reusable workflows from ghcommon:
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
**Status:** Pending
**Priority:** High

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
**Status:** Pending
**Priority:** Medium

**Required Updates:**
- Document CI fix in changelog
- Update README with proper usage examples
- Document testing methodology
- Add troubleshooting section

---

**Last Updated:** 2025-12-19
**Next Review:** After CI fixes complete
