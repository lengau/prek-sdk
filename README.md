# prek SDK for Workshop

A development environment for projects that use [prek](https://github.com/j178/prek),
a fast, dependency-free reimplementation of pre-commit. It installs the `prek`
binary on the workshop PATH so you can run pre-commit-style hooks without
setting up Python environments inside the workshop.

---

## Reference workshop

A minimal workshop:

```yaml
# workshop.yaml
name: dev
base: ubuntu@24.04
sdks:
  - name: prek
    channel: 0.5/stable
```

This demonstrates a basic setup where `prek` is available for running
repository hooks.

---

## Using the SDK

### Prerequisites, project layout

1. The project repository is mounted at `/project` inside the workshop, as
   with any workshop.
2. A `.pre-commit-config.yaml` in the project root defines the hooks `prek`
   runs. See the [upstream configuration docs](https://prek.j178.dev/).
3. `prek` manages hook environments under its own cache directory; nothing
   needs to be set up manually at launch.

### Run hooks

Once the workshop is ready:

```bash
workshop exec -- prek run --all-files
```

or, from within the workshop shell:

```bash
workshop shell
prek run --all-files
```

Hook caches live inside the workshop container. Output (modified files,
reports) is written into the project directory, which is shared with the
host.

---

## Plugs (resources this SDK consumes)

This SDK doesn't define any plugs.

## Slots (resources this SDK provides)

This SDK doesn't define any slots.

---

## Documentation and guidance

- [prek official documentation](https://prek.j178.dev/)
- [prek source repository](https://github.com/j178/prek)

---

## Community and support

- Workshop community on [Matrix](https://matrix.to/#/#documentation:ubuntu.com)
  and [Discourse](https://discourse.ubuntu.com/)
- Please review our [Code of Conduct](https://ubuntu.com/community/ethos/code-of-conduct)
  before participating.

---

## Contributions

All contributions, including code, documentation updates, and issue reports,
are welcome!

- Open issues or pull requests on the repository you obtained this SDK from.

---

## License and copyright

Copyright 2026 Alex Lowe.

The prek SDK is released under the MIT License. The packaged `prek` binary is
released under its upstream licenses; see
https://github.com/j178/prek/blob/main/LICENSE for details.
