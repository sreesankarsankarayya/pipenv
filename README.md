# Guide to Pipenv, Pyenv, and Docker in MacOS / WSL on Win 11/10

> The same approach without WSL works on MacOS

> _Refer to the [Appendix](#appendix) section for detailed installation and setup instructions for WSL, Docker, Homebrew, and more._

## Introduction
`Pipenv` is a tool for managing Python dependencies, virtual environments, and packaging. It is an alternative to `virtualenv` and `venv`, offering a streamlined experience.

### Installation of Pipenv
```bash
sudo apt update
sudo apt install pipenv
```

### Creating a Pipenv Environment
To initialize a new environment and install dependencies:
```bash
pipenv --python 3.11.9
pipenv install fastapi
```
This will create a `Pipfile` and `Pipfile.lock`, managing dependencies.

### Additional Package Management in Pipenv
#### Installing Specific Packages with Categories
```bash
pipenv install requests==1.2 --categories="for-Test for-Packaging"
pipenv install numpy --categories="for-ML"
```

#### Viewing Installed Packages
```bash
pipenv graph
```

#### Uninstalling a Package
```bash
pipenv uninstall requests --categories="for-Test"
```

### Application Structure
#### `src/app.py`
```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def first_example():
    """
    First FastAPI Example
    """
    return {"Example": "FastAPI"}
```

#### `Pipfile`
```toml
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
requests = "1.2"

[for-packaging]
uvicorn = "*"
fastapi = "*"

[for-ML]
numpy = "*"
```

### Running the Application
```bash
pipenv run uvicorn src.app:app --reload
```

---

# Managing Multiple Python Versions with Pyenv

## Installing Pyenv
```bash
brew update
brew install pyenv
```

### Installing and Switching Python Versions
```bash
pyenv install 3.11
pyenv shell 3.11
python --version
```

### Installing SQLite and Tkinter Support
```bash
sudo apt install libsqlite3-dev python3-tk
brew install python-tk
```

### Using Virtualenv with Pyenv
```bash
pyenv exec pip install virtualenv
virtualenv ~/venvs4py/ve4_ms_abc
source ~/venvs4py/ve4_ms_abc/bin/activate
```

---

# Running Docker Containers in WSL (Kali Linux)

## Installing Docker
```bash
sudo apt install docker.io
sudo systemctl start docker
sudo systemctl enable docker
```

## Running a Simple Web Server
#### `docker-compose.yml`
```yaml
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

### Running the Container
```bash
docker compose up -d
```

### Checking if the Server is Running
```bash
curl -v http://localhost:8081
```

### Stopping the Container
```bash
docker compose down
```

---

# Running GUI Applications in WSL (Kali Linux)

### Installing Win-KeX
```bash
sudo apt install kali-win-kex
```

### Starting the GUI
```bash
kex --win -s
```

---

# Appendix

## A) Setting up WSL 
>_[back to top](#Guide)_

### Installing WSL
```bash
wsl --install
```
This installs the default Linux distribution (Ubuntu). To install Kali Linux specifically, use:
```bash
wsl --install -d kali-linux
```

### Checking Installed Distributions
```bash
wsl -l -v
```

### Setting Default WSL Version
```bash
wsl --set-version kali-linux 2
```

### Updating WSL Kernel
```bash
wsl --update
```

### Starting WSL
```bash
wsl
```

## B) Setting up Homebrew 
>_[back to top](#Guide)_

### Installing Homebrew (Linux)
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### Configuring Homebrew (Linux)
```bash
echo 'eval "$('/home/linuxbrew/.linuxbrew/bin/brew shellenv')"' >> ~/.bashrc
source ~/.bashrc
```

### Verifying Installation (Linux)
```bash
brew --version
```

### Installing Homebrew (MacOS)
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### Configuring Homebrew (MacOS)
```bash
echo 'eval "$('/opt/homebrew/bin/brew shellenv')"' >> ~/.zshrc
source ~/.zshrc
```

### Verifying Installation (MacOS)
```bash
brew --version
```

## C) Accessing Docker Desktop from Kali Linux WSL 
>_[back to top](#Guide)_

### Enable WSL Integration in Docker Desktop
```bash
docker version
```
If the client connects successfully, it should display version details.

### Setting Environment Variable for Docker
```bash
export DOCKER_HOST=tcp://localhost:2375
```
To make this permanent, add it to your `~/.bashrc`:
```bash
echo 'export DOCKER_HOST=tcp://localhost:2375' >> ~/.bashrc
source ~/.bashrc
```

### Running a Test Docker Container
```bash
docker run hello-world
```

<br/>

# Refer
> To execution logs for troubleshoot help [here...](more....md)

