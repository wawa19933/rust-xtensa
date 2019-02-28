-include ../../run-make-fulldeps/tools.mk

# FIXME(eddyb) provide `HOST_RUSTC` and `TARGET_RUSTC`
# instead of hardcoding them everywhere they're needed.
all:
    ifeq ($(IS_MUSL_HOST),1)
	    $(BARE_RUSTC) $(RUSTFLAGS) -Clinker=$(RUSTC_LINKER) foo.rs --out-dir $(TMPDIR)
    else
	    $(BARE_RUSTC) foo.rs --out-dir $(TMPDIR)
    endif
	$(RUSTC) bar.rs --target $(TARGET) --emit dep-info
	$(CGREP) -v "proc-macro source" < $(TMPDIR)/bar.d
