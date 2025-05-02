# Dev Container Env Bug

This repository demonstrates a bug involving environment variables when running the dev container's `postCreateCommand`
script.
This bug affects version 2025.1 of Jetbrains IDEs (tested with IntelliJ IDEA and PyCharm).

## Steps to reproduce

1.  Create a dev container from the main branch of this repository (git@github.com:tygern/devcontainer-env-bug.git).
1.  Watch the output of the `postCreateCommand` in the terminal.
    We would expect the script to print the full value of the `DEMO_VARIABLE` environment variable as defined in
    the [devcontainer.json](./.devcontainer/devcontainer.json) file.
    ```shell
    correctbehavioristoshow=thefullenvironmentvariablevalue
    ```
    But instead the `postCreateCommand` will truncate the value of the `DEMO_VARIABLE` environment variable at the
    equals sign.
    ```shell
    correctbehavioristoshow
    ```

## Notes

-   Once the dev container starts, the value of the `DEMO_VARIABLE` environment variable is correct.
-   Jetbrains version 2024.3.x and earlier of Jetbrains IDEs behave correctly with respect to environment variables in
    the `postCreateCommand`.
-   The dev container CLI behaves correctly with respect to environment variables in the `postCreateCommand`.
    ```shell
    devcontainer up --workspace-folder .
    ```
