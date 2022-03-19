## 2019.08.30

When trying to run `cookiecutter datascience...`, I was getting a `Errno 13 permission denied` error. This was related to permission denied errors in anaconda. Found solution online at [permission denied when using anaconda-navigator...](https://github.com/ContinuumIO/anaconda-issues/issues/10262). 

Solution comes down to manually deleting the folder `.anaconda`. The full path is: `C:\Users\ivan\.anaconda`

Will try the same (i.e. manually delete) for the folder `.cookiecutter_replay` 

It worked!


cookiecutter error message for completeness:

```powershell
(accel_phys) D:\Dropbox\RBT\3NVM1>cookiecutter https://github.com/drivendata/cookiecutter-data-science
You've downloaded C:\Users\ivan\.cookiecutters\cookiecutter-data-science before. Is it okay to delete and re-download it? [yes]: yes
project_name [project_name]: 3nvm1
repo_name [3nvm1]: 
author_name [Your name (or your organization/company/team)]: igad
description [A short description of the project.]: Dipole magnet measurements.
Select open_source_license:
1 - MIT
2 - BSD-3-Clause
3 - No license file
Choose from 1, 2, 3 (1, 2, 3) [1]: 1
s3_bucket [[OPTIONAL] your-bucket-for-syncing-data (do not include 's3://')]: 
aws_profile [default]: 
Select python_interpreter:
1 - python3
2 - python
Choose from 1, 2 (1, 2) [1]: 1
Traceback (most recent call last):
  File "C:\Anaconda3\envs\accel_phys\Scripts\cookiecutter-script.py", line 10, in <module>
    sys.exit(main())
  File "C:\Anaconda3\envs\accel_phys\lib\site-packages\click\core.py", line 764, in __call__
    return self.main(*args, **kwargs)
  File "C:\Anaconda3\envs\accel_phys\lib\site-packages\click\core.py", line 717, in main
    rv = self.invoke(ctx)
  File "C:\Anaconda3\envs\accel_phys\lib\site-packages\click\core.py", line 956, in invoke
    return ctx.invoke(self.callback, **ctx.params)
  File "C:\Anaconda3\envs\accel_phys\lib\site-packages\click\core.py", line 555, in invoke
    return callback(*args, **kwargs)
  File "C:\Anaconda3\envs\accel_phys\lib\site-packages\cookiecutter\cli.py", line 120, in main
    password=os.environ.get('COOKIECUTTER_REPO_PASSWORD')
  File "C:\Anaconda3\envs\accel_phys\lib\site-packages\cookiecutter\main.py", line 87, in cookiecutter
    dump(config_dict['replay_dir'], template_name, context)
  File "C:\Anaconda3\envs\accel_phys\lib\site-packages\cookiecutter\replay.py", line 37, in dump
    with open(replay_file, 'w') as outfile:
PermissionError: [Errno 13] Permission denied: 'C:\\Users\\ivan/.cookiecutter_replay/cookiecutter-data-science.json'
```
