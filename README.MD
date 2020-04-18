## Python script to download all Springer books released for free during the 2020 COVID-19 quarantine

### Usage

Just run the script in the desired folder. It will automatically create a /download/ subfolder and will categorize the books acording the subject.

If you want to manually set a folder to download, insert `folder = 'C:/desired_folder/'` in `main.py`.

The books are now organized in sub folders according to the subject ("English Package Name" column).

Now updated to also download epub files if it's available.

If you want just one or two specific books, get the excel file from the folowing link and download just those: https://resource-cms.springernature.com/springer-cms/rest/v1/content/17858272/data/v4

It took about 4 hours to complete the 409 english books (14 GB, both PDF and epub) on my machine.

### Before Running ###

Make sure you have the following dependencies

```bash
certifi==2020.4.5.1
chardet==3.0.4
et-xmlfile==1.0.1
idna==2.9
jdcal==1.4.1
numpy==1.18.2
openpyxl==3.0.3
pandas==1.0.3
python-dateutil==2.8.1
pytz==2019.3
requests==2.23.0
six==1.14.0
tqdm==4.45.0
urllib3==1.25.8
xlrd==1.2.0
```

### Usage in a virtual environment:

```bash
python3 -m venv .venv
. .venv/bin/activate
pip install -r requirements.txt
python3 main.py
```

### Virtual environment on Windows:

```
//install virtual environment first
pip install virtualenv

//navigate to pip directory 
virtualenv venv -p C:\Python27\python.exe

python -m venv .venv
cd .venv/Scripts
activate.bat
cd ../..
pip install -r requirements.txt
python main.py
```

### Source:
* https://group.springernature.com/gp/group/media/press-releases/freely-accessible-textbook-initiative-for-educators-and-students/17858180?utm_medium=social&utm_content=organic&utm_source=facebook&utm_campaign=SpringerNature_&sf232256230=1
* https://www.springernature.com/gp/librarians/news-events/all-news-articles/industry-news-initiatives/free-access-to-textbooks-for-institutions-affected-by-coronaviru/17855960
* https://resource-cms.springernature.com/springer-cms/rest/v1/content/17858272/data/v4

Thanks Springer!

## Docker container to do all the work

Considering you cloned the repo in a folder, as:
```bash
cd \home\[user]\workspace`
git clone https://github.com/alexgand/springer_free_books.git
cd springer_free_books
mkdir downloads
```
You can run the scripts like that:

```bash
docker build . -t springer-image
docker run --rm -v [local_download_folder]:/app/downloads springer-image
```

and the downloads will be at [local_download_folder]

