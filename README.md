# Python
import urllib.request
import urllib.error
import re
try:
    url = "http://search.dangdang.com/?key=%C9%EE%B6%C8%D1%A7%CF%B0&category_path=01.00.00.00.00.00&page_index=1"
    header = {'user-agent':'Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/58.0.3029.110 Safari/537.36 SE 2.X MetaSr 1.0'}  
    pat='><a title=" (.*?)" href="(.*?)"'
    for i in range(1,37):
        mn = i
        url = "http://search.dangdang.com/?key=%C9%EE%B6%C8%D1%A7%CF%B0&category_path=01.00.00.00.00.00&page_index="+str(mn)
    data = urllib.request.urlopen("http://search.dangdang.com/?key=%C9%EE%B6%C8%D1%A7%CF%B0&category_path=01.00.00.00.00.00&page_index="+str(mn)).read().decode("GB2312","ignore")
    rst = re.compile(pat).findall(data)
except urllib.error.URLError as e:
    if hasattr(e,"code"):
        print(e.code)
    if hasattr(e,"reason"):
        print(e.reason)
fh = open("D:\\Program Files\\My spider\\books.csv","w",encoding='utf8')
for i in range(0,len(rst)):
    print(rst[i])
    fh.write(str(rst[i])+"\n")
fh.close()

