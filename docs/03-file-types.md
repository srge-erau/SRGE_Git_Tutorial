# File types and data

[← Tutorial home](../README.md)

Track files needed to understand and reproduce the project. Keep generated outputs and machine-specific state out of ordinary Git history. Extension alone is not enough: a small CSV test fixture and a multi-gigabyte CSV dataset need different handling.

## File type reference

| Type | Common extensions | Suggested location | Git treatment |
| --- | --- | --- | --- |
| Documentation | `.md`, `.txt` | Root or `docs/` | Track useful instructions |
| Source code | `.py`, `.m`, `.cpp`, `.c`, `.h`, `.hpp` | `src/`, `include/` | Track |
| Shell scripts | `.sh`, `.ps1` | `scripts/` | Track; state platform requirements |
| Notebooks | `.ipynb` | `notebooks/` | Track; clear bulky outputs before committing |
| Configuration | `.yaml`, `.yml`, `.json`, `.toml`, `.ini` | `configs/` or tool-required location | Track non-secret settings |
| Dependencies | `pyproject.toml`, `requirements.txt`, lock files | Root or package directory | Track according to tool conventions |
| Small tabular fixtures | `.csv`, `.tsv` | `tests/fixtures/`, `examples/` | Track if small and shareable |
| Scientific data | `.mat`, `.h5`, `.hdf5`, `.npy`, `.npz`, `.parquet` | `data/` | External storage or LFS for large inputs |
| Robotics recordings | `.bag`, `.db3`, `.mcap` | External data storage | Usually external; document retrieval |
| Model weights | `.pt`, `.pth`, `.onnx`, `.ckpt` | External model storage | External or LFS; record version/checksum |
| Documentation images | `.svg`, `.png`, `.jpg` | `assets/` | Track small relevant images |
| Papers/media | `.pdf`, `.mp4`, `.zip` | `docs/` or external storage | Consider size and sharing rights |
| Build/cache files | `.o`, `.obj`, `.pyc`, `.asv` | Build/cache directories | Ignore |
| Local credentials | `.env`, keys, tokens | Local only | Ignore; provide a sanitized `.env.example` if useful |

## Use .gitignore deliberately

Copy [the starter template](../templates/gitignore-template.txt) into your project's root as `.gitignore`. Review it first: it ignores `data/raw/`, `data/processed/`, and `results/`. Put intentionally tracked fixtures in `tests/fixtures/` or `examples/`.

A `.gitignore` prevents matching untracked files from being added by default. It does not remove files already tracked or erase past commits. To stop tracking a generated file while keeping the local copy:

```bash
git rm --cached path/to/generated-file
git add .gitignore
git commit -m "chore: stop tracking generated output"
```

If a credential was committed, revoke or rotate it promptly and contact the maintainer about removing it from history. Deleting the working file does not remove the earlier copy.

## Large data and Git LFS

GitHub blocks ordinary Git files larger than 100 MiB. Git LFS stores pointer files in Git and keeps the content separately; its storage, bandwidth, and per-file limits depend on the account plan. External storage may fit large research datasets better.

For a project that has selected LFS, install Git LFS and configure the actual patterns you need **before adding those files**. This example tracks `.mat` files under `data/lfs/`:

```bash
git lfs install
git lfs track "data/lfs/*.mat"
git add .gitattributes
git add data/lfs/example.mat
git commit -m "data: track example MATLAB dataset with LFS"
```

The example file must exist. Commit `.gitattributes` so collaborators use the same rules. Tracking a pattern does not migrate previously committed files; plan any history migration with the maintainer.

For external datasets, create `data/README.md` with the source URL or DOI, access instructions, dataset version, expected filenames, schema, units, checksums when available, and preprocessing command. Keep a small shareable fixture for examples.

## References

- [GitHub large-file limits](https://docs.github.com/en/repositories/working-with-files/managing-large-files/about-large-files-on-github)
- [Git Large File Storage](https://docs.github.com/en/repositories/working-with-files/managing-large-files/about-git-large-file-storage)
- [Ignoring files](https://docs.github.com/en/get-started/git-basics/ignoring-files)
