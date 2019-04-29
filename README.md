# How to publish your library to PyPi ?

## Step 0 :: Clone your project project with [Git command](https://git-scm.com/)
```
$git clone https://github.com/kachain2019/demo-helloworld-library.git
$cd demo-helloworld-library
```

## Step 1 :: create file `.pypirc` 
 * สร้างไฟล์ `.pypirc` ไว้ที่ path C:\Users\<ชื่อ> ดูจาก cmd ก็ได้ครับ แล้วเอาโค้ดข่้างล่างไปวาง

```
[distutils]
index-servers =
  pypi

[pypi]
repository=https://upload.pypi.org/legacy/
username=username
password=password
```

* Register your account at [PyPi](https://pypi.org/)


## Step 2 :: To publish your code into [PyPI](https://pypi.org/)
List of files
* README.md
* LICENSE.txt
* setup.cfg
* setup.py

Edit file `setup.py`
```
from setuptools import setup

setup(
    name="helloworld-library",  // change to your name ชื่อไลบรารี่ของคุณ
    version='1.0',  // change to version as same as tag version
    package_dir={'' : 'src'},
    packages=['HelloWorld'],
    url='https://github.com/kachain2019/demo-helloworld-library', // change to your repository เปลี่ยนเป็น url ของ git คุณ
    author='your name', 
    author_email='your email',
)

```

Add all files and folders to git repo
```
$git status
$git add -A
$git commit -m "Hello First Library"
$git tag 1.0 -m "Add tag for version 1.0"
$git push origin master
$git push origin 1.0
```

Deploy to PyPI
```
$pip install -U pip setuptools twine
$python setup.py sdist
$twine upload dist/*

Uploading distributions to https://upload.pypi.org/legacy/
Uploading helloworld-library-1.0.tar.gz
100%|███████████████████████████████████████████████| 3.76k/3.76k [00:01<00:00, 3.63kB/s]
```

See your library at [PyPi project](https://pypi.org/manage/projects/)
