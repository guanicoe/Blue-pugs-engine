# Crawler (beta) v0.2



      /$$$$$$                                   /$$
     /$$__  $$                                 | $$
    | $$  \__/  /$$$$$$  /$$$$$$  /$$  /$$  /$$| $$  /$$$$$$   /$$$$$$
    | $$       /$$__  $$|____  $$| $$ | $$ | $$| $$ /$$__  $$ /$$__  $$
    | $$      | $$  \__/ /$$$$$$$| $$ | $$ | $$| $$| $$$$$$$$| $$  \__/
    | $$    $$| $$      /$$__  $$| $$ | $$ | $$| $$| $$_____/| $$
    |  $$$$$$/| $$     |  $$$$$$$|  $$$$$/$$$$/| $$|  $$$$$$$| $$
     \______/ |__/      \_______/ \_____/\___/ |__/ \_______/|__/


## Description

This small utility script was made to crawl websites for email addresses. It uses **multiprocessing** threads to get multiple workers to scrape the web pages, extract emails and links, and dumps them in a *.csv file.

It is quite easy to use but is in early development stage. I don't know if it will be maintained. This will depend on whether it is a useful script or not.  The code may be considered as ugly, but it works (at least for me). So if you can make it better, go ahead. 

## Installation

#### Prerequisite

Everything you need to install is in the `requirements.txt` file. However, some noteworthy libraries are listed below 

```
beautifulsoup4
lxml
pandas
pyzmq
```

You just need to download the repository, and install the requirements. 

```sh
git clone https://github.com/guenicoe/crawler
python3 -m pip install -r requirements.txt
chmod +x crawler.py
```

## Usage

There is only one required flag `-u` which sets the target url.

#### Defaults

- **WORKERS**: By default, the number of worker is set to **40**, modify this `-w` depending on you CPU power (more is not always better). 
- **LIMIT**: By default, there is a set of **5000** page limit to scan. This is a lot! But if the website has fewer accessible page, it will scan all. You can nevertheless specify no limits `-ul`.
- **DOMAIN**: By default, if **no** domain are specified, the script will just crawl and may go outside the website (* there is an exclusion list hard coded) . You can specify `-d` one or more domains to stick with.
- **OUTPUT DIRECTORY**: Two files are output. One with unique emails and a second with two columns: email, URL (with duplicates). The latter enables you to see where the email was found.
- **HEADER**: By default, web pages don't allow bots to scrape them. The header sent is thus: `{'User-Agent': 'Mozilla/5.0 (Windows NT 6.1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/41.0.2228.0 Safari/537.3'}`. You can modify this `-H` by stating a dictionary 



```sh
sage: crawler.py [-h] -u URL [-d DOMAIN [DOMAIN ...]] [-w WORKERS] [-l LIMIT]
                  [-ul] [-o OUTPUT_DIR] [-H HEADER] [-v] [--version]

Process some integers.

optional arguments:
  -h, --help            show this help message and exit
  -u URL, --url URL     Url to crawl
  -d DOMAIN [DOMAIN ...], --domain DOMAIN [DOMAIN ...]
                        Domain name to keep in scope (ex: -d domain1,
                        domain2). The first domain will be used as name for
                        output. If not specified, the script will go outside
                        the webite (will take a long time as it will basically
                        scan the internet). The output name will be guessed
                        from url.
  -w WORKERS, --workers WORKERS
                        Number of workers (default: 40)
  -l LIMIT, --limit LIMIT
                        Limite the number of pages to crawl (default: 5000)
  -ul, --unlimit        Do not limit the number of pages to scan. This will
                        disable -l flag. (default: False)
  -o OUTPUT_DIR, --output-dir OUTPUT_DIR
                        Specify which directory to save the date. (default is
                        URL)
  -H HEADER, --header HEADER
                        Specify which directory to save the date. (default is
                        "{'User-Agent': 'Mozilla/5.0 (Windows NT 6.1)
                        AppleWebKit/537.36 (KHTML, like Gecko)
                        Chrome/41.0.2228.0 Safari/537.3'}")
  -v, --verbose         TODO: Will define the level of verbose. Sets the level
                        of logging
  --version             Returns the version number

```

## TO-DO

- finish README :)





G

