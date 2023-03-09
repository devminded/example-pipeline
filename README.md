# example-pipeline

Just a completely crazy "everything in one go" mega pipeline. This may not be a good practice, but it's used here to demonstrate flow-control.

For example we can trigger 2 commit builds very close to each other and the first one will be cancelled. On the other hand, if we commit 3 times with a few minutes apart so that it reaches the test stage, the first instance will continue to run the tests, the second will abort and the third (last) will wait for the first to finish before continuing.

In a real world scenario we would only perform the commit build, deploy to dev and then record the artifacts and manifests in a central registry. We would then trigger a different set of deployment pipelines with the "version/commit" of the build we want to deploy. Doing it that way means we can separate build and deployment. The hard part will be linking them so that the audit trail persists, we can do that by referencing the commit id.
