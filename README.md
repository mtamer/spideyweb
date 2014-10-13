SpideyWeb
=========
![alt tag](https://github.com/mtamer/spideyweb/blob/master/web.png)

Simple WebCrawler

# Usage

Crawl any Website and return specific results you are looking for.

## Example

``` python
 page = 25
    while page <= max_pages:
    # Add any URL here and make sure to increment depending on the "Next page";
    # I used the website UsedOttawa and looking for a car = Honda;
        url = 'http://www.usedottawa.com/classifieds/all/' + str(page) + '?description=honda' 
        source_code = requests.get(url)
        plain_text = source_code.text
        soup = BeautifulSoup(plain_text)
        # Make sure to go to Website and find specific tags with the classes you want to grab.
        for link in soup.findAll('a',{'itemprop':'name'}):
            href = "http://www.usedottawa.com/" + link.get('href')
            title = link.string
            print(href)
            print(title)
            get_single_item_data(href)
            page+=25
```
## To Install

 1. apt-get install python-bs4
 2. pip install requests

##Notes
Make sure to look at your're URL you are crawling and look at how it changes when visiting the next page and the next page... etc.

