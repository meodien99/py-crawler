# py-crawler
A simple web crawler by python (v 3.4+)

Note: I'm using python version [3.4](https://www.python.org/download/releases/3.4.0/), It's recommended to use the same version or newer(tested with 3.5) in your machine to make sure everything runs perfectly.

# Installation
I used [aiohttp](https://github.com/KeepSafe/aiohttp) for asyncio between client and HTTP server. If you didn't install it. Simply run command below, it will automatically install required packages:
```
$ python3.4 -m pip install -r requirements
```

Run test file:
```
$ python3.4 test.py 
........'http://127.0.0.1:41893' failed after 1 tries
....redirect limit reached for 'http://127.0.0.1:46191/bar' from 'http://127.0.0.1:46191/foo'
..[FetchStatistic(url='http://127.0.0.1:34929/foo', next_url='http://127.0.0.1:34929/baz', status=302, exception=None, size=0, content_type=None, encoding=None, num_urls=0, num_new_urls=0),
 FetchStatistic(url='http://127.0.0.1:34929/bar', next_url='http://127.0.0.1:34929/baz', status=302, exception=None, size=0, content_type=None, encoding=None, num_urls=0, num_new_urls=0),
 FetchStatistic(url='http://127.0.0.1:34929/baz', next_url='http://127.0.0.1:34929/quux', status=302, exception=None, size=0, content_type=None, encoding=None, num_urls=0, num_new_urls=0),
 FetchStatistic(url='http://127.0.0.1:34929/quux', next_url=None, status=404, exception=None, size=14, content_type=None, encoding=None, num_urls=0, num_new_urls=0)]
...
----------------------------------------------------------------------
Ran 17 tests in 0.136s

OK

```

# Usage
Py-crawler support some options:
```
$ python3.4 crawl.py -h

usage: crawl.py [-h] [--iocp] [--select] [--max_redirect N] [--max_tries N]
                [--max_tasks N] [--exclude REGEX] [--strict] [--lenient] [-v]
                [-q]
                [roots [roots ...]]

Web crawler

positional arguments:
  roots             Root URL (may be repeated)

optional arguments:
  -h, --help        show this help message and exit
  --iocp            Use IOCP event loop (Windows only)
  --select          Use Select event loop instead of default
  --max_redirect N  Limit redirection chains (for 301, 302 etc.)
  --max_tries N     Limit retries on network errors
  --max_tasks N     Limit concurrent connections
  --exclude REGEX   Exclude matching URLs
  --strict          Strict host matching (default)
  --lenient         Lenient host matching
  -v, --verbose     Verbose logging (repeat for more verbose)
  -q, --quiet       Only log errors

```
# Example
```
$ python3.4 crawl.py http://dantri.com.vn

http://dantri.com.vn/xa-hoi/ngay-buon-tren-song-han-me-cha-khoc-ngat-goi-ten-con-20160605153755679.htm 200 text/html UTF-8 71743 8/78
http://dantri.com.vn/xa-hoi/nghia-tinh-nhung-ngu-dan-het-long-cuu-nguoi-gap-nan-2016060518414644.htm 200 text/html UTF-8 70638 4/75
http://dantri.com.vn/xa-hoi/tau-du-lich-cho-gan-50-nguoi-lat-tren-song-han-20160604213622051.htm 200 text/html UTF-8 86643 15/81
http://dantri.com.vn/xa-hoi/tim-thay-ca-3-nguoi-mat-tich-ket-thuc-cong-tac-cuu-nan-vu-lat-tau-20160605155917774.htm 200 text/html UTF-8 76447 15/78
http://www.dantri.com.vn 302 redirect http://dantri.com.vn/
Finished 169 urls in 8.963 secs (max_tasks=100) (0.189 urls/sec/task)
       166 html
  12726551 html_bytes
         1 other
      7881 other_bytes
         2 redirect
Todo: 3709
Done: 169
Date: Sun Jun  5 22:15:32 2016 local time

```
Note: Currently, you need to use `ctrl + C` to stop crawling immediately.
