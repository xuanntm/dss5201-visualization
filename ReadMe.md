# Document for new course

## Create environment and install necessary libraries
```shell
python3.12 -m venv venv-dsa2101
source venv-dsa2101/bin/activate
pip install -r requirements.txt
```

## export to html file
```shell
jupyter nbconvert --to html week1_lecture.ipynb
```