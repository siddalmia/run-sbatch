# run-sbatch
Wrapper over sbatch

This is a simple wrapper over sbatch which allows you to run slurm batched jobs.

Before running makes sure :
- change email domain to your own domain
- add the following to your bashrc/bash_profile : `export PATH="$PATH_TO_THIS_SCRIPT":$PATH` 

```
  run-sbatch --job job.sh
  run-sbatch --gpu 0 --job-name test_script --job job.sh --job-opts "--job_arg1 arg1 --job_arg2 arg2 arg3"
  run-sbatch --gpu 0 --job-name test_script --job-lang python3 --job job.py --job-opts "--job_arg1 arg1 --job_arg2 arg2 arg3"
```

OPTIONS CURRENTLY SUPPORTED :
```
              --exclude  <exclude_list> : List of nodes to exclude (eg. islpc18,islpc19 or islpc[30-33]).
              --nodes    <node_list>    : List of nodes to include (eg. islpc18,islpc19 or islpc[30-33]).
              --job-name <job_name>     : Name of the job (also sets the slurm output filename).
              --job-lang <job_lang>     : Language the job is written, typically how you call the job (eg. python or python3 or perl etc.), Default is bash.
              --job-log  <job_log_dir>  : Directory path for the job output file.
              --job-opts <job_opts>     : The options needed for the job to run (NOTE: Options should be inside quotes("")).
              --gpu      <ngpus>        : Number of GPUs[0-n] needed for the job, Default is 1.
```

Thanks to kaldi for providing a shell argument parser (https://github.com/kaldi-asr/kaldi).
