# run-sbatch (wrapper over sbatch)

This is a simple wrapper over sbatch which allows you to run slurm batched jobs without changing any of your existing scripts/code.

Before running makes sure :
- change email domain to your own domain (currently set to andrew.cmu.edu)
- add the following to your bashrc/bash_profile : `export PATH="$PATH_TO_THIS_SCRIPT":$PATH` 

EXAMPLES
- If you have shell script that you normally as `./job.sh --job_arg1 arg1 --job_arg2 arg2 arg3`, you can use `run-sbatch` to run it as a slurm batched process - `run-sbatch --gpu 0 --job-name test_script --job job.sh --job-opts "--job_arg1 arg1 --job_arg2 arg2 arg3"` 

- If you have python program you normally run as `python3 job.py --job_arg1 arg1 --job_arg2 arg2 arg3`, you can use `run-sbatch` to run it as a slurm batched process - `run-sbatch.sh --gpu 0 --job-name test_script --job-lang python3 --job job.py --job-opts "--job_arg1 arg1 --job_arg2 arg2 arg3"` 

- It will support any language you provide what to use to call the `job` in `--job-lang`.

OPTIONS (Currently Supported):
```
              --exclude  <exclude_list> : List of nodes to exclude (eg. islpc18,islpc19 or islpc[30-33]).
              --nodes    <node_list>    : List of nodes to include (eg. islpc18,islpc19 or islpc[30-33]).
              --job-name <job_name>     : Name of the job (also sets the slurm output filename).
              --job-lang <job_lang>     : Language the job is written, typically how you call the job (eg. python or python3 or perl etc.), Default is bash.
              --job-log  <job_log_dir>  : Directory path for the job output file.
              --job-opts <job_opts>     : The options needed for the job to run (NOTE: Options should be inside quotes("")).
              --gpu      <ngpus>        : Number of GPUs[0-n] needed for the job, Default is 1.
```

Make sure your `$PATH`, `$LD_LIBRARY_PATH` and other environment variables are set such that it would run the code will execute in the assigned node (eg. if you are using Anaconda or have CUDA in a non-traditional place).

Thanks to the authors of Kaldi (https://github.com/kaldi-asr/kaldi) for providing a wonderful shell argument parser.

The current support is **limited**, please feel free to add (don't forget to send in a pull request :)) or email me if you need any more options/features.
