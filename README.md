# apx-fractal-task-collection

A collection of custom fractal tasks.

## Development instructions

This instructions are only relevant *after* you completed both the `copier
copy` command and the git/GitLab/GitHub initialization phase - see
[README](https://github.com/fractal-analytics-platform/fractal-tasks-template#readme)
for details.

1. It is recommended to work from an isolated Python virtual environment:
```console
# Create the virtual environment in the folder venv
python -m venv venv
# Activate the Python virtual environment
source venv/bin/activate
# Deactivate the virtual environment, when you don't need it any more
deactivate
```
2. You can install your package locally as in:
```console
# Install only apx_fractal_task_collection:
python -m pip install -e .
# Install both apx_fractal_task_collection and development dependencies (e.g. pytest):
python -m pip install -e ".[dev]"
```

3. Enjoy developing the package.

4. The template already includes a sample task ("Thresholding Task"). Whenever
you change its input parameters or docstring, re-run
```console
python src/apx_fractal_task_collection/dev/update_manifest.py
git add src/apx_fractal_task_collection/__FRACTAL_MANIFEST__.json
git commit -m'Update `__FRACTAL_MANIFEST__.json`'
git push origin main
```

5. If you add a new task, you should also add a new item to the `task_list`
property in `src/apx_fractal_task_collection/__FRACTAL_MANIFEST__.json`. A minimal example
may look like
```json
    {
      "name": "My Second Task",
      "executable": "my_second_task.py",
      "input_type": "zarr",
      "output_type": "zarr"
    }
```

6. Run the test suite (with somewhat verbose logging) through
```console
python -m pytest --log-cli-level info -s
```
7. Build the package through
```console
python -m build
```
This command will create the release distribution files in the `dist` folder.
The wheel one (ending with `.whl`) is the one you can use to collect your tasks
within Fractal.
