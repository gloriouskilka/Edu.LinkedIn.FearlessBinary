# Edu.LinkedIn.FearlessBinary

A working x86_64 emulator and ELF64 reader in Python, built as a teaching artefact, where the
instruction set is defined in a specification rather than scattered through the code.

**This snapshot is intentionally empty while the next release is prepared.**

The public repository here is a release-only snapshot, not a mirror: development happens in a
private repository and lands here as versions rather than as a diary. The previous snapshot was
removed because it had gone stale - it carried decoding defects that have since been found and
fixed, and a half-corrected published version is worse than none.

Two of the defects it carried, as an idea of what "stale" meant:

- `41 90` is `xchg r8d, eax`, and that snapshot decoded it as a no-op and did not perform the
  swap at all.
- `66 B8 34 12` is a four-byte `mov ax, 0x1234`; it read a four-byte immediate instead of two,
  came out six bytes long, and swallowed the instruction that followed.

Both were found by pointing something outside the project at it - `objdump`, and the processor
this all runs on. That is what the next release is about.

Licensed under the MIT License - see [LICENSE](LICENSE).
