This directory contains code for MPI "Hello world" example, Slurm
batch script, compilation instructions, and output. While the some of
the details are specific to SDSC's Expanse system (e.g., compiler and
library version, Slurm partition names, etc.) you should be able to
easily adapt to other environments.

Place the following near the top of your script, but after Slurm
specifications

```
echo "---- BEGIN Slurm, hardware and environment information ----"
echo "SLURM_JOB_ID: $SLURM_JOB_ID"
echo "SLURM_JOB_NODELIST: $SLURM_JOB_NODELIST"
lscpu
printenv
echo "---- END Slurm, hardware and environment information ----"
echo
```

Add the following before the executing your code

```
timedate_start=`date`
epoch_start=`date +%s`
```

And the following after executing your code

```
timedate_end=`date`
epoch_end=`date +%s`
t_elapsed=$((epoch_end-epoch_start))

echo
echo "---- BEGIN time and date information ----"
echo "Job started at $timedate_start / epoch time: $epoch_start"
echo "Job ended at $timedate_end / epoch time: $epoch_end"
echo "Elapsed time: $t_elapsed"
echo "---- END time and date information ----"
```
