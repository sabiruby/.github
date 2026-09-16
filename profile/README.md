# SabiRuby

A virtual machine for [mruby](https://github.com/mruby/mruby) bytecode, written in Rust.
"Sabi" is Japanese for rust.

It runs the bytecode the reference compiler produces and is checked against mruby's own test
suite. The VM is pure `no_std` Rust with no unsafe code, so the same crate builds for the
desktop, the browser and microcontrollers, and embeds in a Rust application with
`cargo add sabiruby` — no C toolchain, no FFI.

## Repositories

| repository | what it is |
|---|---|
| [sabiruby](https://github.com/sabiruby/sabiruby) | the VM, the reference mruby compiler as a crate, and the `sabiruby` command line tool |
| [sabiruby-playground](https://github.com/sabiruby/sabiruby-playground) | write Ruby in the browser and watch the VM run it, one instruction at a time — [open it](https://sabiruby.github.io/sabiruby-playground/) |
| [rubevy](https://github.com/sabiruby/rubevy) | SabiRuby inside the [Bevy](https://bevy.org) game engine: one VM, a Ruby task per entity, scripts that ask the game and wait |
| [rubevy_games](https://github.com/sabiruby/rubevy_games) | games whose brains are Ruby, editable while they run — [SabiRuby Battle](https://sabiruby.github.io/rubevy_games/sabibots/) and [Garden](https://sabiruby.github.io/rubevy_games/garden/) play in the browser |

## What it is for

* **Embedding Ruby in Rust.** The VM is an ordinary Rust value: no global state, exceptions as
  `Result`, native methods as Rust functions. A host runs it a budget of instructions at a time.
* **Scripts that cannot take the host down.** Many scripts share one VM as scheduled tasks with
  priorities; a script that never yields is preempted, one that raises ends alone, and time
  limits bound what the instruction count cannot see.
* **Seeing the machine.** The VM's state is plain data, so a host can show what a script is
  spending and where it stands — the playground's inspector, or a HUD in a game.
* **One program, several machines.** The same bytecode runs on a PC, in a browser and on a
  microcontroller-class device.

Speed is not the goal; SabiRuby is slower than the C mruby. The goal is a Ruby that is safe to
embed, easy to build, and transparent enough to learn from.
