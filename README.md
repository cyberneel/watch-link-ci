# watch-link-ci

Linker-as-a-service for building arm64e watchOS binaries from Linux.

The open-source `lld` cannot link arm64e Mach-O (pointer-authentication needs chained
fixups it doesn't implement), so this repo runs Apple's linker on a GitHub macOS runner
for that single step. Compiled object files are pulled from the dev box **over Tailscale**
and never appear in this repo or its artifacts; only the linked executable is returned.

The workflow is public and inspectable. The only secret is a Tailscale auth key.
