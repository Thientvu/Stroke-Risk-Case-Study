## Setting up environment
1. Make sure you have [Miniconda](https://docs.anaconda.com/free/miniconda/) installed on your computer
2. Create a new environment that uses python 3.9.18
    ```
    conda create --name [your_env_name] python=3.9.18
    ```
3. Once the environment has been created, activate your enviroment
    ```
    conda activate [your_env_name]
    ```
4. Confirm your env has been created
    ```
    conda env list
    ```
5. Make sure pip is up-to-date
    ```
    pip install --upgrade pip
    ```
6. Install necessary python packages
    ```
    pip install -r requirements.txt
    ```