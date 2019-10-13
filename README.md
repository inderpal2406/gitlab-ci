# GitLab-CI
This repository is to practise .gitlab-ci.yml file examples.

Currently examples are being practised from this [link](https://medium.com/faun/ci-cd-essentials-from-scratch-with-gitlab-61502acf318e)

## Key points to remember while writing `.gitlab-ci.yml` file.
* `.gitlab-ci.yml` file must contain at least one job.  If there are no jobs defined in it when we push the code to Gitlab, Gitlab runner will throw an error saying `invalid yaml configuration`. the job running fails. This is verified in ex7,8,9. Even if we define a single hidden job, it'll fail. So, a visible job is mandatory.
* You can see all the pipelines of a project under the Pipelines section of Gitlab repository.
* You can see the logs of the job by clicking on it. ✅ button indicates your job ran successfully. Yellow indicates your job is paused. ❌ indicates that your job failed. Blue represents that the job is running.
* Any .gitlab-ci.yml supported keywords can't be used as a job name. Kywords such as `image, stages, script, except, only, variables, etc.`
* Multiple jobs in same stage run in parallel.
* We cannot assign same name to different jobs. If we do so, gitlab will traverse through the `.gitlab-ci.yml` file and skip the same name job and will execute the last job with same name in the sequence.
* Pipeline ids start with `#`
* Stage names will be displayed on top of pipeline GUI.
* Job names will be displayed below stage names in pipeline GUI.
* Every stage need not have a job declared.
* Order of the job execution is based on the order of stage declaration. If a stage doesn’t have at least one job defined, Then that stage will be skipped and goes to next stage job.
* A stage can have multiple jobs defined.
* Gitlab assigns jobs to `test` stage by default if we don't define a `stages` in `.gitlab-ci.yml` file. This is when we don't specify `stage` in our job as well. If we define a `stage` in our job, but that `stage` is not defined in `stages`, then we'll get an error.
* If you have defined a stage called “test”, and define a job without stage added in it, Then the job will run under test stage since the default stage is test.
* If you haven’t defined the test stage and create a job without stage defined in it, Then Gitlab pipeline will throw an error like yaml invalid and will ask you to specify the stage for the job as shown below.
* `only` will accept regular expressions. If your commit matches with regular expression, pipeline gets activated and jobs will executed as per configuration.
* `only` and `except` are inclusive. If both only and except are defined in a job specification, the ref is filtered by only and except.
* `only` and `except` allow the use of regular expressions (using Ruby regexp syntax).
* `only` and `except` allow to specify a repository path to filter jobs for forks.
* The default value for `when` attribute is `on-success`
* The default value for `allow_failure` attribute is `false`. That is the reason if any error occurs in pipeline remaining jobs will be skipped.


## Keywords used in `.gitlab-ci.yml`  file.
* script
* stages
* stage
* only
* except
