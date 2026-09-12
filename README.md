# simc-builds

Prebuilt [SimulationCraft](https://github.com/simulationcraft/simc) command-line
binaries, one release per simc commit, for a private Localbots sim pool.
The pool's server pins a simc commit; its workers fetch the matching build
from here instead of compiling it themselves.

Every release is named after the simc commit it was built from
(`simc-<sha>`) and carries:

- `simc-<sha>-linux-x64.zip`, `simc-<sha>-windows-x64.zip`,
  `simc-<sha>-macos-arm64.zip` — the `simc` binary, built with
  `SC_NO_NETWORKING=ON` (it cannot fetch anything; the pool feeds it text),
  plus simc's `LICENSE` files and a `BUILD.txt` with the exact commit.
- `simc-<sha>-dbc.zip` — `engine/dbc/generated/*.inc`, the data files a
  Localbots *server* reads next to the binary (workers do not need them).
- `simc-<sha>-source.tar.gz` — the corresponding source, verbatim.
- `SHA256SUMS`.

SimulationCraft is licensed under the GNU GPLv3; these are unmodified
builds of the linked commit, and the source of each build is attached to
its release. This is not an official SimulationCraft distribution — for
that, and for everything else, see [simulationcraft.org](https://www.simulationcraft.org/).

Builds run nightly for the head of simc's current branch and on demand
(`workflow_dispatch` with a commit sha). A release that already exists is
not rebuilt.
