# Getting to Pipenv
This is a step by step work walkthrough reference on managing multiple Python versions Env and finally the solution with a combination of pyenv &amp; pipenv 

## Kali-Linux 

> Using pipenv for application dev

[`PipEnv` Documentation](https://python.land/virtual-environments/pipenv#:~:text=We%20can%20use%20pip%20%28or%20even%20better%3A%20pipx%29,ensure%20that%20you%20won%E2%80%99t%20interfere%20with%20system-wide%20packages.)


src.app

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def first_example():
    """
    FG Example First Fast API Example 
    """
    return {"GFG Example": "FastAPI"}

```
the Pipfile that gets generated!

```Pipfile
[[source]]
url = "https://pypi.org/simple"
verify_ssl = true
name = "pypi"

[packages]
fastapi = "*"

[dev-packages]
flask = "*"

[requires]
python_version = "3.11"
python_full_version = "3.11.9"

[for-test]
uvicorn = "*"
flask = "*"

[for-packaging]
uvicorn = "*"
fastapi = "*"

```

<details>
<summary>PipEnv is the best Distilled!</summary>

```bash
Alternatively, run a command inside the virtualenv with pipenv run.
Installing flask==1.2...
✔ Installation Succeeded
Installing requests==1.1...
✔ Installation Succeeded
To activate this project's virtualenv, run pipenv shell.
Alternatively, run a command inside the virtualenv with pipenv run.
Installing dependencies from Pipfile.lock (c883f9)...
All dependencies are now up-to-date!
Upgrading flask==1.2, requests==1.1 in  dependencies.
Building requirements...
Resolving dependencies...
✘ Locking Failed!
⠹ Locking dev-packages...ERROR:pip.subprocessor:python setup.py egg_info exited with 1
[ResolutionFailure]:   File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/resolver.py", line 451, in main
[ResolutionFailure]:       _main(
[ResolutionFailure]:   File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/resolver.py", line 436, in _main
[ResolutionFailure]:       resolve_packages(
[ResolutionFailure]:   File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/resolver.py", line 400, in resolve_packages
[ResolutionFailure]:       results, resolver = resolve_deps(
[ResolutionFailure]:       ^^^^^^^^^^^^^
[ResolutionFailure]:   File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/utils/resolver.py", line 967, in resolve_deps
[ResolutionFailure]:       results, hashes, internal_resolver = actually_resolve_deps(
[ResolutionFailure]:       ^^^^^^^^^^^^^^^^^^^^^^
[ResolutionFailure]:   File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/utils/resolver.py", line 735, in actually_resolve_deps    
[ResolutionFailure]:       resolver.resolve()
[ResolutionFailure]:   File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/utils/resolver.py", line 460, in resolve
[ResolutionFailure]:       raise ResolutionFailure(message=e)
Your dependencies could not be resolved. You likely have a mismatch in your sub-dependencies.
You can use $ pipenv run pip install <requirement_name> to bypass this mechanism, then run $ pipenv graph to inspect the versions actually installed in the   
virtualenv.
Hint: try $ pipenv lock --pre if it is a pre-release dependency.
ERROR: metadata generation failed

Your dependencies could not be resolved. You likely have a mismatch in your sub-dependencies.                                                                 
You can use $ pipenv run pip install <requirement_name> to bypass this mechanism, then run $ pipenv graph to inspect the versions actually installed in the 
virtualenv.
Hint: try $ pipenv lock --pre if it is a pre-release dependency.
ERROR: Failed to lock Pipfile.lock!

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ pipenv lock --pre
Locking [packages] dependencies...
Locking [dev-packages] dependencies...
Locking [for-packaging] dependencies...
Building requirements...
Resolving dependencies...
✔ Success!
Locking [for-test] dependencies...                                                                                                                            
Building requirements...
Resolving dependencies...
✔ Success!
Updated Pipfile.lock (a1366542bc02152509d99204105d2741c39491e89ba1aef5ad49469f46c883f9)!                                                                      

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ pipenv install flask==1.2 requests==1.1 --dev
To activate this project's virtualenv, run pipenv shell.
Alternatively, run a command inside the virtualenv with pipenv run.
Installing flask==1.2...
✔ Installation Succeeded
Installing requests==1.1...
✔ Installation Succeeded
To activate this project's virtualenv, run pipenv shell.
Alternatively, run a command inside the virtualenv with pipenv run.
Installing dependencies from Pipfile.lock (c883f9)...
All dependencies are now up-to-date!
Upgrading flask==1.2, requests==1.1 in  dependencies.
Building requirements...
Resolving dependencies...
✘ Locking Failed!
⠦ Locking dev-packages...CRITICAL:pipenv.patched.pip._internal.resolution.resolvelib.factory:Could not find a version that satisfies the requirement flask==1.2 (from versions: 0.1,
0.2, 0.3, 0.3.1, 0.4, 0.5, 0.5.1, 0.5.2, 0.6, 0.6.1, 0.7, 0.7.1, 0.7.2, 0.8, 0.8.1, 0.9, 0.10, 0.10.1, 0.11, 0.11.1, 0.12, 0.12.1, 0.12.2, 0.12.3, 0.12.4,    
0.12.5, 1.0, 1.0.1, 1.0.2, 1.0.3, 1.0.4, 1.1.0, 1.1.1, 1.1.2, 1.1.3, 1.1.4, 2.0.0rc1, 2.0.0rc2, 2.0.0, 2.0.1, 2.0.2, 2.0.3, 2.1.0, 2.1.1, 2.1.2, 2.1.3, 2.2.0,
2.2.1, 2.2.2, 2.2.3, 2.2.4, 2.2.5, 2.3.0, 2.3.1, 2.3.2, 2.3.3, 3.0.0, 3.0.1, 3.0.2, 3.0.3, 3.1.0)
[ResolutionFailure]:   File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/resolver.py", line 451, in main
[ResolutionFailure]:       _main(
[ResolutionFailure]:   File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/resolver.py", line 436, in _main
[ResolutionFailure]:       resolve_packages(
[ResolutionFailure]:   File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/resolver.py", line 400, in resolve_packages
[ResolutionFailure]:       results, resolver = resolve_deps(
[ResolutionFailure]:       ^^^^^^^^^^^^^
[ResolutionFailure]:   File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/utils/resolver.py", line 967, in resolve_deps
[ResolutionFailure]:       results, hashes, internal_resolver = actually_resolve_deps(
[ResolutionFailure]:       ^^^^^^^^^^^^^^^^^^^^^^
[ResolutionFailure]:   File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/utils/resolver.py", line 735, in actually_resolve_deps    
[ResolutionFailure]:       resolver.resolve()
[ResolutionFailure]:   File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/utils/resolver.py", line 460, in resolve
[ResolutionFailure]:       raise ResolutionFailure(message=e)
Your dependencies could not be resolved. You likely have a mismatch in your sub-dependencies.
You can use $ pipenv run pip install <requirement_name> to bypass this mechanism, then run $ pipenv graph to inspect the versions actually installed in the   
virtualenv.
Hint: try $ pipenv lock --pre if it is a pre-release dependency.
ERROR: No matching distribution found for flask==1.2

Your dependencies could not be resolved. You likely have a mismatch in your sub-dependencies.                                                                 
You can use $ pipenv run pip install <requirement_name> to bypass this mechanism, then run $ pipenv graph to inspect the versions actually installed in the 
virtualenv.
Hint: try $ pipenv lock --pre if it is a pre-release dependency.
ERROR: Failed to lock Pipfile.lock!

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ pipenv lock --pre
Locking [packages] dependencies...
Locking [dev-packages] dependencies...
Locking [for-test] dependencies...
Building requirements...
Resolving dependencies...
✔ Success!
Locking [for-packaging] dependencies...                                                                                                                       
Building requirements...
Resolving dependencies...
✔ Success!
Updated Pipfile.lock (a1366542bc02152509d99204105d2741c39491e89ba1aef5ad49469f46c883f9)!                                                                      

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ pipenv install flask==1.2--dev
To activate this project's virtualenv, run pipenv shell.
Alternatively, run a command inside the virtualenv with pipenv run.
Installing flask==1.2--dev...
Traceback (most recent call last):
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/patched/pip/_vendor/packaging/requirements.py", line 36, in __init__
    parsed = _parse_requirement(requirement_string)
             ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/patched/pip/_vendor/packaging/_parser.py", line 62, in parse_requirement       
    return _parse_requirement(Tokenizer(source, rules=DEFAULT_RULES))
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/patched/pip/_vendor/packaging/_parser.py", line 80, in _parse_requirement      
    url, specifier, marker = _parse_requirement_details(tokenizer)
                             ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/patched/pip/_vendor/packaging/_parser.py", line 124, in _parse_requirement_details
    marker = _parse_requirement_marker(
             ^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/patched/pip/_vendor/packaging/_parser.py", line 145, in _parse_requirement_marker
    tokenizer.raise_syntax_error(
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/patched/pip/_vendor/packaging/_tokenizer.py", line 167, in raise_syntax_error  
    raise ParserSyntaxError(
pipenv.patched.pip._vendor.packaging._tokenizer.ParserSyntaxError: Expected end or semicolon (after version specifier)
    flask==1.2--dev
         ~~~~~^

The above exception was the direct cause of the following exception:

Traceback (most recent call last):
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/patched/pip/_internal/req/constructors.py", line 362, in _parse_req_string     
    return get_requirement(req_as_string)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/patched/pip/_internal/utils/packaging.py", line 45, in get_requirement
    return Requirement(req_string)
           ^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/patched/pip/_vendor/packaging/requirements.py", line 38, in __init__
    raise InvalidRequirement(str(e)) from e
pipenv.patched.pip._vendor.packaging.requirements.InvalidRequirement: Expected end or semicolon (after version specifier)
    flask==1.2--dev
         ~~~~~^

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/home/sree/.pyenv/versions/3.11.11/bin/pipenv", line 8, in <module>
    sys.exit(cli())
             ^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/vendor/click/core.py", line 1157, in __call__
    return self.main(*args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/cli/options.py", line 52, in main
    return super().main(*args, **kwargs, windows_expand_args=False)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/vendor/click/core.py", line 1078, in main
    rv = self.invoke(ctx)
         ^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/vendor/click/core.py", line 1688, in invoke
    return _process_result(sub_ctx.command.invoke(sub_ctx))
                           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/vendor/click/core.py", line 1434, in invoke
    return ctx.invoke(self.callback, **ctx.params)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/vendor/click/core.py", line 783, in invoke
    return __callback(*args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/vendor/click/decorators.py", line 92, in new_func
    return ctx.invoke(f, obj, *args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/vendor/click/core.py", line 783, in invoke
    return __callback(*args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/cli/command.py", line 207, in install
    do_install(
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/routines/install.py", line 310, in do_install
    new_packages, _ = handle_new_packages(
                      ^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/routines/install.py", line 58, in handle_new_packages
    pkg_requirement, _ = expansive_install_req_from_line(
                         ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/utils/dependencies.py", line 1031, in expansive_install_req_from_line
    parts = parse_req_from_line(pip_line, line_source)
            ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/patched/pip/_internal/req/constructors.py", line 379, in parse_req_from_line   
    req: Optional[Requirement] = _parse_req_string(req_as_string)
                                 ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/patched/pip/_internal/req/constructors.py", line 376, in _parse_req_string     
    raise InstallationError(msg)
pipenv.patched.pip._internal.exceptions.InstallationError: Invalid requirement: 'flask==1.2--dev': Expected end or semicolon (after version specifier)        
    flask==1.2--dev
         ~~~~~^

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ pipenv install flask==1.2 --dev
To activate this project's virtualenv, run pipenv shell.
Alternatively, run a command inside the virtualenv with pipenv run.
Installing flask==1.2...
✔ Installation Succeeded
To activate this project's virtualenv, run pipenv shell.
Alternatively, run a command inside the virtualenv with pipenv run.
Installing dependencies from Pipfile.lock (c883f9)...
All dependencies are now up-to-date!
Upgrading flask==1.2 in  dependencies.
Building requirements...
Resolving dependencies...
✘ Locking Failed!
⠦ Locking dev-packages...CRITICAL:pipenv.patched.pip._internal.resolution.resolvelib.factory:Could not find a version that satisfies the requirement flask==1.2 (from versions: 0.1,
0.2, 0.3, 0.3.1, 0.4, 0.5, 0.5.1, 0.5.2, 0.6, 0.6.1, 0.7, 0.7.1, 0.7.2, 0.8, 0.8.1, 0.9, 0.10, 0.10.1, 0.11, 0.11.1, 0.12, 0.12.1, 0.12.2, 0.12.3, 0.12.4,    
0.12.5, 1.0, 1.0.1, 1.0.2, 1.0.3, 1.0.4, 1.1.0, 1.1.1, 1.1.2, 1.1.3, 1.1.4, 2.0.0rc1, 2.0.0rc2, 2.0.0, 2.0.1, 2.0.2, 2.0.3, 2.1.0, 2.1.1, 2.1.2, 2.1.3, 2.2.0,
2.2.1, 2.2.2, 2.2.3, 2.2.4, 2.2.5, 2.3.0, 2.3.1, 2.3.2, 2.3.3, 3.0.0, 3.0.1, 3.0.2, 3.0.3, 3.1.0)
[ResolutionFailure]:   File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/resolver.py", line 451, in main
[ResolutionFailure]:       _main(
[ResolutionFailure]:   File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/resolver.py", line 436, in _main
[ResolutionFailure]:       resolve_packages(
[ResolutionFailure]:   File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/resolver.py", line 400, in resolve_packages
[ResolutionFailure]:       results, resolver = resolve_deps(
[ResolutionFailure]:       ^^^^^^^^^^^^^
[ResolutionFailure]:   File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/utils/resolver.py", line 967, in resolve_deps
[ResolutionFailure]:       results, hashes, internal_resolver = actually_resolve_deps(
[ResolutionFailure]:       ^^^^^^^^^^^^^^^^^^^^^^
[ResolutionFailure]:   File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/utils/resolver.py", line 735, in actually_resolve_deps    
[ResolutionFailure]:       resolver.resolve()
[ResolutionFailure]:   File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/utils/resolver.py", line 460, in resolve
[ResolutionFailure]:       raise ResolutionFailure(message=e)
Your dependencies could not be resolved. You likely have a mismatch in your sub-dependencies.
You can use $ pipenv run pip install <requirement_name> to bypass this mechanism, then run $ pipenv graph to inspect the versions actually installed in the   
virtualenv.
Hint: try $ pipenv lock --pre if it is a pre-release dependency.
ERROR: No matching distribution found for flask==1.2

Your dependencies could not be resolved. You likely have a mismatch in your sub-dependencies.                                                                 
You can use $ pipenv run pip install <requirement_name> to bypass this mechanism, then run $ pipenv graph to inspect the versions actually installed in the   
virtualenv.
Hint: try $ pipenv lock --pre if it is a pre-release dependency.
ERROR: Failed to lock Pipfile.lock!

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ pipenv run pip install flask
Collecting flask
  Downloading flask-3.1.0-py3-none-any.whl.metadata (2.7 kB)
Collecting Werkzeug>=3.1 (from flask)
  Downloading werkzeug-3.1.3-py3-none-any.whl.metadata (3.7 kB)
Collecting Jinja2>=3.1.2 (from flask)
  Downloading jinja2-3.1.5-py3-none-any.whl.metadata (2.6 kB)
Collecting itsdangerous>=2.2 (from flask)
  Downloading itsdangerous-2.2.0-py3-none-any.whl.metadata (1.9 kB)
Requirement already satisfied: click>=8.1.3 in /home/sree/.local/share/virtualenvs/src_11-kfL92l5e/lib/python3.11/site-packages (from flask) (8.1.8)
Collecting blinker>=1.9 (from flask)
  Downloading blinker-1.9.0-py3-none-any.whl.metadata (1.6 kB)
Collecting MarkupSafe>=2.0 (from Jinja2>=3.1.2->flask)
  Downloading MarkupSafe-3.0.2-cp311-cp311-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (4.0 kB)
Downloading flask-3.1.0-py3-none-any.whl (102 kB)
Downloading blinker-1.9.0-py3-none-any.whl (8.5 kB)
Downloading itsdangerous-2.2.0-py3-none-any.whl (16 kB)
Downloading jinja2-3.1.5-py3-none-any.whl (134 kB)
Downloading werkzeug-3.1.3-py3-none-any.whl (224 kB)
Downloading MarkupSafe-3.0.2-cp311-cp311-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (23 kB)
Installing collected packages: MarkupSafe, itsdangerous, blinker, Werkzeug, Jinja2, flask
Successfully installed Jinja2-3.1.5 MarkupSafe-3.0.2 Werkzeug-3.1.3 blinker-1.9.0 flask-3.1.0 itsdangerous-2.2.0

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ cat Pipfile
[[source]]
url = "https://pypi.org/simple"
verify_ssl = true
name = "pypi"

[packages]

[dev-packages]

[requires]
python_version = "3.11"
python_full_version = "3.11.9"

[for-test]
uvicorn = "*"

[for-packaging]
uvicorn = "*"

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ pipenv install flask --dev
To activate this project's virtualenv, run pipenv shell.
Alternatively, run a command inside the virtualenv with pipenv run.
Installing flask...
✔ Installation Succeeded
To activate this project's virtualenv, run pipenv shell.
Alternatively, run a command inside the virtualenv with pipenv run.
Installing dependencies from Pipfile.lock (c883f9)...
All dependencies are now up-to-date!
Upgrading flask in  dependencies.
Building requirements...
Resolving dependencies...
✔ Success!
Building requirements...                                                                                                                                      
Resolving dependencies...
✔ Success!
To activate this project's virtualenv, run pipenv shell.                                                                                                      
Alternatively, run a command inside the virtualenv with pipenv run.
Installing dependencies from Pipfile.lock (cbdf32)...
All dependencies are now up-to-date!
Installing dependencies from Pipfile.lock (cbdf32)...
Installing dependencies from Pipfile.lock (cbdf32)...

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ pipenv install flask --categories="for-test for-packaging"
To activate this project's virtualenv, run pipenv shell.
Alternatively, run a command inside the virtualenv with pipenv run.
Installing flask...
✔ Installation Succeeded
To activate this project's virtualenv, run pipenv shell.
Alternatively, run a command inside the virtualenv with pipenv run.
Installing dependencies from Pipfile.lock (cbdf32)...
Installing dependencies from Pipfile.lock (cbdf32)...
All dependencies are now up-to-date!
Upgrading flask in  dependencies.
Building requirements...
Resolving dependencies...
✔ Success!
Building requirements...                                                                                                                                      
Resolving dependencies...
✔ Success!
Upgrading flask in  dependencies.                                                                                                                             
Building requirements...
Resolving dependencies...
✔ Success!
Building requirements...                                                                                                                                      
Resolving dependencies...
✔ Success!
To activate this project's virtualenv, run pipenv shell.                                                                                                      
Alternatively, run a command inside the virtualenv with pipenv run.
Installing dependencies from Pipfile.lock (fa7ded)...
Installing dependencies from Pipfile.lock (fa7ded)...
All dependencies are now up-to-date!
Installing dependencies from Pipfile.lock (fa7ded)...
Installing dependencies from Pipfile.lock (fa7ded)...

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ cat Pipfile
[[source]]
url = "https://pypi.org/simple"
verify_ssl = true
name = "pypi"

[packages]

[dev-packages]
flask = "*"

[requires]
python_version = "3.11"
python_full_version = "3.11.9"

[for-test]
uvicorn = "*"
flask = "*"

[for-packaging]
uvicorn = "*"
flask = "*"

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ pipenv uninstall flask --categories="for-packaging"
Removed flask from Pipfile.
Building requirements...
Resolving dependencies...
✔ Success!
Uninstalling flask...                                                                                                                                         
Found existing installation: Flask 3.1.0
Uninstalling Flask-3.1.0:
  Successfully uninstalled Flask-3.1.0


┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ cat Pipfile
[[source]]
url = "https://pypi.org/simple"
verify_ssl = true
name = "pypi"

[packages]

[dev-packages]
flask = "*"

[requires]
python_version = "3.11"
python_full_version = "3.11.9"

[for-test]
uvicorn = "*"
flask = "*"

[for-packaging]
uvicorn = "*"

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ pipenv install fastapi 
To activate this project's virtualenv, run pipenv shell.
Alternatively, run a command inside the virtualenv with pipenv run.
Installing fastapi...
✔ Installation Succeeded
To activate this project's virtualenv, run pipenv shell.
Alternatively, run a command inside the virtualenv with pipenv run.
Installing dependencies from Pipfile.lock (d98e66)...
All dependencies are now up-to-date!
Upgrading fastapi in  dependencies.
Building requirements...
Resolving dependencies...
✔ Success!
Building requirements...                                                                                                                                      
Resolving dependencies...
✔ Success!
To activate this project's virtualenv, run pipenv shell.                                                                                                      
Alternatively, run a command inside the virtualenv with pipenv run.
Installing dependencies from Pipfile.lock (180521)...
All dependencies are now up-to-date!
Installing dependencies from Pipfile.lock (180521)...

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ cat Pipfile
[[source]]
url = "https://pypi.org/simple"
verify_ssl = true
name = "pypi"

[packages]
fastapi = "*"

[dev-packages]
flask = "*"

[requires]
python_version = "3.11"
python_full_version = "3.11.9"

[for-test]
uvicorn = "*"
flask = "*"

[for-packaging]
uvicorn = "*"

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ pipenv graph
blinker==1.9.0
fastapi==0.115.8
├── pydantic 
│   ├── annotated-types 
│   ├── pydantic_core 
│   │   └── typing_extensions 
│   └── typing_extensions 
├── starlette 
│   └── anyio 
│       ├── idna 
│       ├── sniffio 
│       └── typing_extensions 
└── typing_extensions 
itsdangerous==2.2.0
Jinja2==3.1.5
└── MarkupSafe 
uvicorn==0.34.0
├── click 
└── h11 
Werkzeug==3.1.3
└── MarkupSafe 

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ pipenv install --dev
To activate this project's virtualenv, run pipenv shell.
Alternatively, run a command inside the virtualenv with pipenv run.
Installing dependencies from Pipfile.lock (180521)...
Installing dependencies from Pipfile.lock (180521)...

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ pipenv install --for-test
To activate this project's virtualenv, run pipenv shell.
Alternatively, run a command inside the virtualenv with pipenv run.
Installing --for-test...
Traceback (most recent call last):
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/patched/pip/_vendor/packaging/requirements.py", line 36, in __init__
    parsed = _parse_requirement(requirement_string)
             ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/patched/pip/_vendor/packaging/_parser.py", line 62, in parse_requirement       
    return _parse_requirement(Tokenizer(source, rules=DEFAULT_RULES))
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/patched/pip/_vendor/packaging/_parser.py", line 71, in _parse_requirement      
    name_token = tokenizer.expect(
                 ^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/patched/pip/_vendor/packaging/_tokenizer.py", line 142, in expect
    raise self.raise_syntax_error(f"Expected {expected}")
          ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/patched/pip/_vendor/packaging/_tokenizer.py", line 167, in raise_syntax_error  
    raise ParserSyntaxError(
pipenv.patched.pip._vendor.packaging._tokenizer.ParserSyntaxError: Expected package name at the start of dependency specifier
    --for-test
    ^

The above exception was the direct cause of the following exception:

Traceback (most recent call last):
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/patched/pip/_internal/req/constructors.py", line 362, in _parse_req_string     
    return get_requirement(req_as_string)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/patched/pip/_internal/utils/packaging.py", line 45, in get_requirement
    return Requirement(req_string)
           ^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/patched/pip/_vendor/packaging/requirements.py", line 38, in __init__
    raise InvalidRequirement(str(e)) from e
pipenv.patched.pip._vendor.packaging.requirements.InvalidRequirement: Expected package name at the start of dependency specifier
    --for-test
    ^

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/home/sree/.pyenv/versions/3.11.11/bin/pipenv", line 8, in <module>
    sys.exit(cli())
             ^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/vendor/click/core.py", line 1157, in __call__
    return self.main(*args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/cli/options.py", line 52, in main
    return super().main(*args, **kwargs, windows_expand_args=False)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/vendor/click/core.py", line 1078, in main
    rv = self.invoke(ctx)
         ^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/vendor/click/core.py", line 1688, in invoke
    return _process_result(sub_ctx.command.invoke(sub_ctx))
                           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/vendor/click/core.py", line 1434, in invoke
    return ctx.invoke(self.callback, **ctx.params)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/vendor/click/core.py", line 783, in invoke
    return __callback(*args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/vendor/click/decorators.py", line 92, in new_func
    return ctx.invoke(f, obj, *args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/vendor/click/core.py", line 783, in invoke
    return __callback(*args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/cli/command.py", line 207, in install
    do_install(
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/routines/install.py", line 310, in do_install
    new_packages, _ = handle_new_packages(
                      ^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/routines/install.py", line 58, in handle_new_packages
    pkg_requirement, _ = expansive_install_req_from_line(
                         ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/utils/dependencies.py", line 1031, in expansive_install_req_from_line
    parts = parse_req_from_line(pip_line, line_source)
            ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/patched/pip/_internal/req/constructors.py", line 379, in parse_req_from_line   
    req: Optional[Requirement] = _parse_req_string(req_as_string)
                                 ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/patched/pip/_internal/req/constructors.py", line 376, in _parse_req_string     
    raise InstallationError(msg)
pipenv.patched.pip._internal.exceptions.InstallationError: Invalid requirement: '--for-test': Expected package name at the start of dependency specifier      
    --for-test
    ^

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ pipenv install --categories="for-test"
To activate this project's virtualenv, run pipenv shell.
Alternatively, run a command inside the virtualenv with pipenv run.
Installing dependencies from Pipfile.lock (180521)...

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ pipenv graph
fastapi==0.115.8
├── pydantic 
│   ├── annotated-types 
│   ├── pydantic_core 
│   │   └── typing_extensions 
│   └── typing_extensions 
├── starlette 
│   └── anyio 
│       ├── idna 
│       ├── sniffio 
│       └── typing_extensions 
└── typing_extensions 
Flask==3.1.0
├── blinker 
├── click 
├── itsdangerous 
├── Jinja2 
│   └── MarkupSafe 
└── Werkzeug 
    └── MarkupSafe
uvicorn==0.34.0
├── click 
└── h11 

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ pipenv install --categories="for-packaging"
To activate this project's virtualenv, run pipenv shell.
Alternatively, run a command inside the virtualenv with pipenv run.
Installing dependencies from Pipfile.lock (180521)...

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ pipenv graph
fastapi==0.115.8
├── pydantic 
│   ├── annotated-types 
│   ├── pydantic_core 
│   │   └── typing_extensions 
│   └── typing_extensions 
├── starlette 
│   └── anyio 
│       ├── idna 
│       ├── sniffio 
│       └── typing_extensions 
└── typing_extensions 
Flask==3.1.0
├── blinker 
├── click 
├── itsdangerous 
├── Jinja2 
│   └── MarkupSafe 
└── Werkzeug 
    └── MarkupSafe
uvicorn==0.34.0
├── click 
└── h11 

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ cat Pipfile 
[[source]]
url = "https://pypi.org/simple"
verify_ssl = true
name = "pypi"

[packages]
fastapi = "*"

[dev-packages]
flask = "*"

[requires]
python_version = "3.11"
python_full_version = "3.11.9"

[for-test]
uvicorn = "*"
flask = "*"

[for-packaging]
uvicorn = "*"

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ pipenv verify
Pipfile.lock is up-to-date.

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ pipenv sync
To activate this project's virtualenv, run pipenv shell.
Alternatively, run a command inside the virtualenv with pipenv run.
Installing dependencies from Pipfile.lock (180521)...
All dependencies are now up-to-date!

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ pipenv check
Checking PEP 508 requirements...
Passed!
Checking Pipfile.lock packages for vulnerabilities...
+============================================================================================================================================================+

                               /$$$$$$            /$$
                              /$$__  $$          | $$
           /$$$$$$$  /$$$$$$ | $$  \__//$$$$$$  /$$$$$$   /$$   /$$
          /$$_____/ |____  $$| $$$$   /$$__  $$|_  $$_/  | $$  | $$
         |  $$$$$$   /$$$$$$$| $$_/  | $$$$$$$$  | $$    | $$  | $$
          \____  $$ /$$__  $$| $$    | $$_____/  | $$ /$$| $$  | $$
          /$$$$$$$/|  $$$$$$$| $$    |  $$$$$$$  |  $$$$/|  $$$$$$$
         |_______/  \_______/|__/     \_______/   \___/   \____  $$
                                                          /$$  | $$
                                                         |  $$$$$$/
  by pyup.io                                              \______/

+============================================================================================================================================================+

 REPORT

  Safety v2.3.2 is scanning for Vulnerabilities...
  Scanning dependencies in your files:

  -> /tmp/src_11-kfL92l5eii3ryoib_requirements.txt

  Found and scanned 9 packages
  Timestamp 2025-02-16 02:11:22
  0 vulnerabilities found
  0 vulnerabilities ignored
+============================================================================================================================================================+

 No known security vulnerabilities found.

+============================================================================================================================================================+

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ pipenv shell
Launching subshell in virtual environment...
 source /home/sree/.local/share/virtualenvs/src_11-kfL92l5e/bin/activate
┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$  source /home/sree/.local/share/virtualenvs/src_11-kfL92l5e/bin/activate

┌──(src_11-kfL92l5e)(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ which python
/home/sree/.local/share/virtualenvs/src_11-kfL92l5e/bin/python

┌──(src_11-kfL92l5e)(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ python --version
Python 3.11.9

┌──(src_11-kfL92l5e)(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ which pip
/home/sree/.local/share/virtualenvs/src_11-kfL92l5e/bin/pip

┌──(src_11-kfL92l5e)(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ exit
exit

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ which python 
/home/sree/.pyenv/shims/python

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ which pip
/home/sree/.pyenv/shims/pip

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ pipenv --rm
Removing virtualenv (/home/sree/.local/share/virtualenvs/src_11-kfL92l5e)...
                                                                                                                                                              
┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ pipenv graph
Traceback (most recent call last):
  File "/home/sree/.pyenv/versions/3.11.11/bin/pipenv", line 8, in <module>
    sys.exit(cli())
             ^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/vendor/click/core.py", line 1157, in __call__
    return self.main(*args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/cli/options.py", line 52, in main
    return super().main(*args, **kwargs, windows_expand_args=False)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/vendor/click/core.py", line 1078, in main
    rv = self.invoke(ctx)
         ^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/vendor/click/core.py", line 1688, in invoke
    return _process_result(sub_ctx.command.invoke(sub_ctx))
                           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/vendor/click/core.py", line 1434, in invoke
    return ctx.invoke(self.callback, **ctx.params)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/vendor/click/core.py", line 783, in invoke
    return __callback(*args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/vendor/click/decorators.py", line 92, in new_func
    return ctx.invoke(f, obj, *args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/vendor/click/core.py", line 783, in invoke
    return __callback(*args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/cli/command.py", line 587, in graph
    do_graph(state.project, bare=bare, json=json, json_tree=json_tree, reverse=reverse)
  File "/home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pipenv/routines/graph.py", line 37, in do_graph
    cmd_args = [python_path, str(pipdeptree_path), "-l"]
                ^^^^^^^^^^^
UnboundLocalError: cannot access local variable 'python_path' where it is not associated with a value

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ cat Pipfile
[[source]]
url = "https://pypi.org/simple"
verify_ssl = true
name = "pypi"

[packages]
fastapi = "*"

[dev-packages]
flask = "*"

[requires]
python_version = "3.11"
python_full_version = "3.11.9"

[for-test]
uvicorn = "*"
flask = "*"

[for-packaging]
uvicorn = "*"

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ pip install --categories="for-packaging"

Usage:
  pip install [options] <requirement specifier> [package-index-options] ...
  pip install [options] -r <requirements file> [package-index-options] ...
  pip install [options] [-e] <vcs project url> ...
  pip install [options] [-e] <local project path> ...
  pip install [options] <archive url/path> ...

no such option: --categories

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ pipenv install --categories="for-packaging"
Creating a virtualenv for this project
Pipfile: /mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11/Pipfile
Using /home/sree/.pyenv/versions/3.11.9/bin/python33.11.9 to create virtualenv...
⠼ Creating virtual environment...created virtual environment CPython3.11.9.final.0-64 in 266ms
  creator CPython3Posix(dest=/home/sree/.local/share/virtualenvs/src_11-kfL92l5e, clear=False, no_vcs_ignore=False, global=False)
  seeder FromAppData(download=False, pip=bundle, setuptools=bundle, wheel=bundle, via=copy, app_data_dir=/home/sree/.local/share/virtualenv)
    added seed packages: pip==25.0.1, setuptools==75.8.0, wheel==0.45.1
  activators BashActivator,CShellActivator,FishActivator,NushellActivator,PowerShellActivator,PythonActivator

✔ Successfully created virtual environment!
Virtualenv location: /home/sree/.local/share/virtualenvs/src_11-kfL92l5e                                                                                      
To activate this project's virtualenv, run pipenv shell.
Alternatively, run a command inside the virtualenv with pipenv run.
Installing dependencies from Pipfile.lock (180521)...

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ pipenv graph
uvicorn==0.34.0
├── click 
└── h11 

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ pipenv run uvicorn src.app:app --reload
INFO:     Will watch for changes in these directories: ['/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11']
INFO:     Uvicorn running on http://127.0.0.1:8000 (Press CTRL+C to quit)
INFO:     Started reloader process [42672] using StatReload
Process SpawnProcess-1:
Traceback (most recent call last):
  File "/home/sree/.pyenv/versions/3.11.9/lib/python3.11/multiprocessing/process.py", line 314, in _bootstrap
    self.run()
  File "/home/sree/.pyenv/versions/3.11.9/lib/python3.11/multiprocessing/process.py", line 108, in run
    self._target(*self._args, **self._kwargs)
  File "/home/sree/.local/share/virtualenvs/src_11-kfL92l5e/lib/python3.11/site-packages/uvicorn/_subprocess.py", line 80, in subprocess_started
    target(sockets=sockets)
  File "/home/sree/.local/share/virtualenvs/src_11-kfL92l5e/lib/python3.11/site-packages/uvicorn/server.py", line 66, in run
    return asyncio.run(self.serve(sockets=sockets))
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.9/lib/python3.11/asyncio/runners.py", line 190, in run
    return runner.run(main)
           ^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.9/lib/python3.11/asyncio/runners.py", line 118, in run
    return self._loop.run_until_complete(task)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.9/lib/python3.11/asyncio/base_events.py", line 654, in run_until_complete
    return future.result()
           ^^^^^^^^^^^^^^^
  File "/home/sree/.local/share/virtualenvs/src_11-kfL92l5e/lib/python3.11/site-packages/uvicorn/server.py", line 70, in serve
    await self._serve(sockets)
  File "/home/sree/.local/share/virtualenvs/src_11-kfL92l5e/lib/python3.11/site-packages/uvicorn/server.py", line 77, in _serve
    config.load()
  File "/home/sree/.local/share/virtualenvs/src_11-kfL92l5e/lib/python3.11/site-packages/uvicorn/config.py", line 435, in load
    self.loaded_app = import_from_string(self.app)
                      ^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.local/share/virtualenvs/src_11-kfL92l5e/lib/python3.11/site-packages/uvicorn/importer.py", line 22, in import_from_string
    raise exc from None
  File "/home/sree/.local/share/virtualenvs/src_11-kfL92l5e/lib/python3.11/site-packages/uvicorn/importer.py", line 19, in import_from_string
    module = importlib.import_module(module_str)
             ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/sree/.pyenv/versions/3.11.9/lib/python3.11/importlib/__init__.py", line 126, in import_module
    return _bootstrap._gcd_import(name[level:], package, level)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "<frozen importlib._bootstrap>", line 1204, in _gcd_import
  File "<frozen importlib._bootstrap>", line 1176, in _find_and_load
  File "<frozen importlib._bootstrap>", line 1147, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 690, in _load_unlocked
  File "<frozen importlib._bootstrap_external>", line 940, in exec_module
  File "<frozen importlib._bootstrap>", line 241, in _call_with_frames_removed
  File "/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11/src/app.py", line 1, in <module>
    from fastapi import FastAPI
ModuleNotFoundError: No module named 'fastapi'
^CINFO:     Stopping reloader process [42672]

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ pipenv install fastapi --categories="for-packaging"
To activate this project's virtualenv, run pipenv shell.
Alternatively, run a command inside the virtualenv with pipenv run.
Installing fastapi...
✔ Installation Succeeded
To activate this project's virtualenv, run pipenv shell.
Alternatively, run a command inside the virtualenv with pipenv run.
Installing dependencies from Pipfile.lock (180521)...
All dependencies are now up-to-date!
Upgrading fastapi in  dependencies.
Building requirements...
Resolving dependencies...
✔ Success!
Building requirements...                                                                                                                                      
Resolving dependencies...
✔ Success!
To activate this project's virtualenv, run pipenv shell.                                                                                                      
Alternatively, run a command inside the virtualenv with pipenv run.
Installing dependencies from Pipfile.lock (cac652)...
All dependencies are now up-to-date!
Installing dependencies from Pipfile.lock (cac652)...

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ pipenv run uvicorn src.app:app --reload
INFO:     Will watch for changes in these directories: ['/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11']
INFO:     Uvicorn running on http://127.0.0.1:8000 (Press CTRL+C to quit)
INFO:     Started reloader process [42832] using StatReload
INFO:     Started server process [42864]
INFO:     Waiting for application startup.
INFO:     Application startup complete.
INFO:     127.0.0.1:58304 - "GET /docs HTTP/1.1" 200 OK
INFO:     127.0.0.1:58304 - "GET /openapi.json HTTP/1.1" 200 OK
^CINFO:     Shutting down
INFO:     Waiting for application shutdown.
INFO:     Application shutdown complete.
INFO:     Finished server process [42864]
INFO:     Stopping reloader process [42832]

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ pipenv shell
Launching subshell in virtual environment...
 source /home/sree/.local/share/virtualenvs/src_11-kfL92l5e/bin/activate
┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$  source /home/sree/.local/share/virtualenvs/src_11-kfL92l5e/bin/activate

┌──(src_11-kfL92l5e)(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ unicorn src.app:app --reload
Command 'unicorn' not found, but can be installed with:
sudo apt install unicorn

┌──(src_11-kfL92l5e)(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ uvicorn src.app:app --reload
INFO:     Will watch for changes in these directories: ['/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11']
INFO:     Uvicorn running on http://127.0.0.1:8000 (Press CTRL+C to quit)
INFO:     Started reloader process [43052] using StatReload
INFO:     Started server process [43054]
INFO:     Waiting for application startup.
INFO:     Application startup complete.
INFO:     127.0.0.1:44268 - "GET / HTTP/1.1" 200 OK
INFO:     127.0.0.1:44268 - "GET /favicon.ico HTTP/1.1" 404 Not Found
^CINFO:     Shutting down
INFO:     Waiting for application shutdown.
INFO:     Application shutdown complete.
INFO:     Finished server process [43054]
INFO:     Stopping reloader process [43052]

┌──(src_11-kfL92l5e)(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ exit
exit

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ pipenv shell
Launching subshell in virtual environment...
 source /home/sree/.local/share/virtualenvs/src_11-kfL92l5e/bin/activate
┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$  source /home/sree/.local/share/virtualenvs/src_11-kfL92l5e/bin/activate

┌──(src_11-kfL92l5e)(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ pip list
Package           Version
----------------- -------
annotated-types   0.7.0
anyio             4.8.0
click             8.1.8
fastapi           0.115.8
h11               0.14.0
idna              3.10
pip               25.0.1
pydantic          2.10.6
pydantic_core     2.27.2
setuptools        75.8.0
sniffio           1.3.1
starlette         0.45.3
typing_extensions 4.12.2
uvicorn           0.34.0
wheel             0.45.1

┌──(src_11-kfL92l5e)(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ which pip
/home/sree/.local/share/virtualenvs/src_11-kfL92l5e/bin/pip

┌──(src_11-kfL92l5e)(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ pip freeze >> requirements.txt

┌──(src_11-kfL92l5e)(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ exit
exit

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$ pipenv --rm
Removing virtualenv (/home/sree/.local/share/virtualenvs/src_11-kfL92l5e)...
                                                                                                                                                              
┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/src_11]
└─$
```

</details>

<br/>

> Multiple alternatives of Python versions with pyenv 

```bash
#Install pyenv
brew update
brew install pyenv
```

```bash
python3 --version
pyenv install --list
pyenv install 3.11

pyenv init 

# Add the output into ~/.bashrc as detailed

pyenv shell 3.11

python --version

```
installing sqllite and tkinter

```bash

sudo apt install libsqlite3-dev python3-tk
brew install python-tk

```

installing virtualenv

```bash

pyenv version
python --version
pip --version

pyenv exec pip install virtualenv

virtualenv --version

```

demo #4 with virtual environments

```text
┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ pyenv versions
  system
  3.11.9
* 3.11.11 (set by /home/sree/.pyenv/version)
  3.12.9

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ pyenv local 3.11.9

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ pyenv versions
  system
* 3.11.9 (set by /mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/.python-version)
  3.11.11
  3.12.9

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ python --version
Python 3.11.9

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ pip --version
pip 25.0.1 from /home/sree/.pyenv/versions/3.11.9/lib/python3.11/site-packages/pip (python 3.11)

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ virtualenv --version
virtualenv 20.29.2 from /home/sree/.pyenv/versions/3.11.9/lib/python3.11/site-packages/virtualenv/__init__.py

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ mkdir ~/venvs4py

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ virtualenv ~/venvs4py/ve4_ms_abc
created virtual environment CPython3.11.9.final.0-64 in 165ms
  creator CPython3Posix(dest=/home/sree/venvs4py/ve4_ms_abc, clear=False, no_vcs_ignore=False, global=False)
  seeder FromAppData(download=False, pip=bundle, setuptools=bundle, wheel=bundle, via=copy, app_data_dir=/home/sree/.local/share/virtualenv)
    added seed packages: pip==25.0.1, setuptools==75.8.0, wheel==0.45.1
  activators BashActivator,CShellActivator,FishActivator,NushellActivator,PowerShellActivator,PythonActivator

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ source ~/venvs4py/ve4_ms_abc/bin/activate

┌──(ve4_ms_abc)(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ pip --version
pip 25.0.1 from /home/sree/venvs4py/ve4_ms_abc/lib/python3.11/site-packages/pip (python 3.11)

┌──(ve4_ms_abc)(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ python --version
Python 3.11.9

┌──(ve4_ms_abc)(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ which python
/home/sree/venvs4py/ve4_ms_abc/bin/python

┌──(ve4_ms_abc)(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ pyenv versions
  system
* 3.11.9 (set by /mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/.python-version)
  3.11.11
  3.12.9

┌──(ve4_ms_abc)(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ deactivate 

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ pyenv local 3.11.11

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ python --version
Python 3.11.11

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ pip --version
pip 25.0.1 from /home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/pip (python 3.11)

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ virtualenv --version
virtualenv 20.29.2 from /home/sree/.pyenv/versions/3.11.11/lib/python3.11/site-packages/virtualenv/__init__.py

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ pyenv versions
  system
  3.11.9
* 3.11.11 (set by /mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/.python-version)
  3.12.9

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ virtualenv ~/venvs4py/ve4_ms_Def
created virtual environment CPython3.11.11.final.0-64 in 164ms
  creator CPython3Posix(dest=/home/sree/venvs4py/ve4_ms_Def, clear=False, no_vcs_ignore=False, global=False)
  seeder FromAppData(download=False, pip=bundle, setuptools=bundle, wheel=bundle, via=copy, app_data_dir=/home/sree/.local/share/virtualenv)
    added seed packages: pip==25.0.1, setuptools==75.8.0, wheel==0.45.1
  activators BashActivator,CShellActivator,FishActivator,NushellActivator,PowerShellActivator,PythonActivator

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ source ~/venvs4py/ve4_ms_Def/bin/activate

┌──(ve4_ms_Def)(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ pip --version
pip 25.0.1 from /home/sree/venvs4py/ve4_ms_Def/lib/python3.11/site-packages/pip (python 3.11)

┌──(ve4_ms_Def)(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ which python
/home/sree/venvs4py/ve4_ms_Def/bin/python

┌──(ve4_ms_Def)(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ python --version
Python 3.11.11

┌──(ve4_ms_Def)(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ deactivate

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$
```

demo #3

```text
┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ pyenv versions
  system
* 3.11.9 (set by /mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/.python-version)
  3.11.11
  3.12.9

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ python --version
Python 3.11.9

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ pip --version
pip 25.0.1 from /home/sree/.pyenv/versions/3.11.9/lib/python3.11/site-packages/pip (python 3.11)

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ virtualenv --version
virtualenv 20.29.2 from /home/sree/.pyenv/versions/3.11.9/lib/python3.11/site-packages/virtualenv/__init__.py

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ 
```

demo #2

```text
┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ python --version
Python 3.11.11

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ pyenv versions
  system
  3.11.9
* 3.11.11 (set by /home/sree/.pyenv/version)
  3.12.9

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ pyenv local 3.11.9

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ pyenv versions
  system
* 3.11.9 (set by /mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL/.python-version)
  3.11.11
  3.12.9

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ python --version
Python 3.11.9

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ pip --version
pip 24.0 from /home/sree/.pyenv/versions/3.11.9/lib/python3.11/site-packages/pip (python 3.11)

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$
```

demo #1

```text
┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ pyenv versions
  system
* 3.11.9 (set by /home/sree/.pyenv/version)
  3.11.11

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ pyenv global 3.11.11

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ pyenv versions
  system
  3.11.9
* 3.11.11 (set by /home/sree/.pyenv/version)

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ python --version
Python 3.11.11

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ pyenv global 3.11.9

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ python --version
Python 3.11.9

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ pyenv versions
  system
* 3.11.9 (set by /home/sree/.pyenv/version)
  3.11.11

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$
```

[This is in the bottom comments!](https://stackoverflow.com/questions/2547554/multiple-python-versions-on-the-same-machine)

[pyenv Git](https://github.com/pyenv/pyenv)

<details>

<summary>tl;dr</summary>

```md

he best way that worked for me is using pyenv!
The commands below are for Mac but pretty similar to Linux (see the links below)

#Install pyenv
brew update
brew install pyenv
Let's say you have python 3.7.6 as your primary version on your mac:

python --version 
Output:

Python 3.7.6
Now Install python 3.10
Fist, we can check if it's already there, run:

pyenv install --list
Scroll up (right above anaconda) to check if it's there/installed, if not, run:

pyenv install 3.10
Make sure to run this in the Terminal (add it to ~/.bashrc or ~/.zshrc):

export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init --path)"
eval "$(pyenv init -)"
Now let's run it only on the opened terminal/shell:

pyenv shell 3.10
Now run
python --version

```
</details>

<br/>

> [ -FAILED attempt- ] Multiple alternatives of Python versions with asdf

[Using asdf](https://asdf-vm.com/guide/getting-started.html)

[ref. from StackOverflow](https://stackoverflow.com/questions/2547554/multiple-python-versions-on-the-same-machine)

```bash
brew install asdf
```

```bash
asdf --version
asdf plugin add python
asdf install python 3.11.11
```

> Installing Brew on WSL > Kali-Linux

```bash

sudo apt update
sudo apt install build-essential curl file git

/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Follow the instuction that shows up at the end to set brew to ~.bashrc

# for exmaple

# => Next steps:
# - Run these commands in your terminal to add Homebrew to your PATH:
#     echo >> /home/sree/.bashrc
#     echo 'eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"' >> /home/sree/.bashrc
#     eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"
# - Install Homebrew's dependencies if you have sudo access:
#     sudo apt-get install build-essential
#   For more information, see:
#     https://docs.brew.sh/Homebrew-on-Linux
# - We recommend that you install GCC:
#     brew install gcc
# - Run brew help to get started
# - Further documentation:
#     https://docs.brew.sh

```

> Checking a docker run from the WSL prompt

```yml
version: '3'
services:
  example.org:
    image: flashspys/nginx-static
    container_name: example.org
    ports:
      - 8081:80
    volumes: 
      - ./path2serve:/static
```

```bash

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ docker compose down
[+] Running 2/2
 ✔ Container example.org  Removed                                                                                                           0.4s 
 ✔ Network wsl_default    Removed                                                                                                           0.2s 

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ docker compose up -d
[+] Running 2/2
 ✔ Network wsl_default    Created                                                                                                           0.0s 
 ✔ Container example.org  Started                                                                                                           0.3s 

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ curl -v http://localhost:8080
* Host localhost:8080 was resolved.
* IPv6: ::1
* IPv4: 127.0.0.1
*   Trying [::1]:8080...
* Connected to localhost (::1) port 8080
* using HTTP/1.x
> GET / HTTP/1.1
> Host: localhost:8080
> User-Agent: curl/8.11.0
> Accept: */*
> 
* Request completely sent off
< HTTP/1.1 200 OK
< Server: nginx/1.27.4
< Date: Sat, 15 Feb 2025 18:21:46 GMT
< Content-Type: text/html; charset=utf-8
< Content-Length: 12
< Last-Modified: Sat, 15 Feb 2025 18:15:37 GMT
< Connection: keep-alive
< ETag: "67b0d9c9-c"
< Accept-Ranges: bytes
< 
* Connection #0 to host localhost left intact
God is Great
┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$ docker compose down
[+] Running 2/2
 ✔ Container example.org  Removed                                                                                                           0.4s 
 ✔ Network wsl_default    Removed                                                                                                           0.3s 

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees/OneDrive/Desktop/111/0215_Py-n-Wsl/WSL]
└─$
```

> Accessing docker from WSL Kali-linux

[A Good reference](https://github.com/jtoalu/docker-on-kali-wsl?tab=readme-ov-file)

<details>
<summary>
tl;dr
</summary>

```md

# Docker in Kali on WSL
I have been utilizing Kali on WSL for almost three years now (since Fall 2021). A challenge on https://dodcybersentinel.ctfd.io/ motivated me to learn how to run a Docker image in my Kali on WSL. It turns out that it is easy to run a Docker image in Kali on WSL.
I searched the Internet and found https://learn.microsoft.com/en-us/windows/wsl/tutorials/wsl-containers for the instructions of $${\color{yellow}Get \space started \space \space with \space Docker \space remote \space containers \space on \space WSL \space 2}$$
After downloading and installing the Docker Desktop for Windows from https://docs.docker.com/desktop/wsl/#download and configuring the necessary settings, a Docker image is ready to run in my Kali on WSL as shown by the following screenshot.

![alt text](https://github.com/jtoalu/docker-on-kali-wsl/blob/main/Screenshot%202024-05-22%20164653.png)

The rest of the steps is loading the Docker file through the Kali on WSL terminal with the following commands:
- docker load -i {filename}.tar
- docker images
- docker run -d -p 1234:80 {image_id}
- docker ps

Replace {filename}.tar with the actual filename and {image_id} with the appropriate image ID from the docker images output.

Please see the following screenshot for more information.

![alt text](https://github.com/jtoalu/docker-on-kali-wsl/blob/main/Screenshot%202024-05-22%20170554.png)

A website which was saved into a Docker instance can now be seen on my laptop by accessing http://localhost:1234/ as shown by the following screenshot.

![alt text](https://github.com/jtoalu/docker-on-kali-wsl/blob/main/Screenshot%202024-05-22%20171821.png)

Note to Self: https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax and https://stackoverflow.com/questions/11509830/how-to-add-color-to-githubs-readme-md-file 

```
</details>

<br/>

> Running the Gui over WSL>Kali-Linux

```bash

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees]
└─$ kex --win -s
Command 'kex' not found, but can be installed with:
sudo apt install kali-win-kex

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees]
└─$

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees]
└─$ kex --win -s
Starting Win-KeX server (Win)
Password:
Verify:
Would you like to enter a view-only password (y/n)? n
A view-only password is not used
        Win-KeX server (Win) is running


Win-KeX server sessions:

X DISPLAY #     RFB PORT #      RFB UNIX PATH   PROCESS ID #    SERVER
1               5901                            17040           Xtigervnc

You can use the Win-KeX client (Win) to connect to any of these displays


Starting Win-KeX client (Win)

┌──(sree㉿QuantumA1)-[/mnt/c/Users/srees]
└─$

```
