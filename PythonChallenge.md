Python Challenge
---

## Level 0


    In [21]: 1<<38
    Out[21]: 274877906944



## Level 1

    # src:http://www.pythonchallenge.com/pc/def/map.html
     
    from string import maketrans
    ori = 'abcdefghijklmnopqrstuvwxyz'
    des = 'cdefghijklmnopqrstuvwxyzab'
     
    tbl = maketrans(ori, des)
     
    text = "g fmnc wms bgblr rpylqjyrc gr zw fylb. rfyrq ufyr amknsrcpq ypc dmp. \
            bmgle gr gl zw fylb gq glcddgagclr ylb rfyr'q ufw rfgq rcvr gq qm jmle. \
            sqgle qrpgle.kyicrpylq() gq pcamkkclbcb. lmu ynnjw ml rfc spj."
            
    print text.translate(tbl)
     
    # So, the answer is:
    print 'map'.translate(tbl)
     
    # Output:   ocr


## Level 2 ##


    #src http://www.pythonchallenge.com/pc/def/ocr.html
     
    import requests
    import re
     
    rep = requests.get("http://www.pythonchallenge.com/pc/def/ocr.html")
    html = rep.text
     
    html = ''.join(html.split()) # strip all newline, tab, space
    text = re.findall(r'<!--(.*?)-->', html)[1] # get the second comment
    wc = {}
     
    for i in text:
        wc[i] = 1 if i not in wc else wc[i]+1
     
    l = [i for i in wc if wc[i]==1]
     
    # retrive answer in text in order
    print ''.join(i for i in text if i in l)
    # Output:   equality
```



## Level 3 ##



    #src: http://www.pythonchallenge.com/pc/def/equality.html
    import requests
    import re
     
    rep = requests.get("http://www.pythonchallenge.com/pc/def/equality.html")
    html = rep.text
     
    html = ''.join(html.split()) 
    text = re.findall(r'<!--(.*?)-->', html)[0] 
     
    res = re.findall(r'[^A-Z][A-Z]{3}([a-z])[A-Z]{3}[^A-Z]', text)
    print ''.join(res) 
    # Output:   linkedlist
```

## Level 4 ##

    # src:  http://www.pythonchallenge.com/pc/def/linkedlist.php?nothing=12345
     
    import urllib2
    import re
    link = "http://www.pythonchallenge.com/pc/def/linkedlist.php?nothing=12345"
    # link = "http://www.pythonchallenge.com/pc/def/linkedlist.php?nothing=8022"
    for i in range(400):
        text = urllib2.urlopen(link).read()
        num = re.findall(r"and the next nothing is (\d+)", text)[0]
     
        link = re.sub('\d+',num, link)
        print num + "\t" + link
        
    # Output:   peak.html

## Level 5 ##


    # src: http://www.pythonchallenge.com/pc/def/peak.html
     
    import cPickle as pickle
    import urllib2
    import re
     
    link = "http://www.pythonchallenge.com/pc/def/banner.p"
     
    text = urllib2.urlopen(link).read()
    data = pickle.loads(text)
     
    for line in data:
        print ''.join(i[0]*i[1] for i in line)
     
    # Output:  channel


