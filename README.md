# ǰ��

�뿴����������Ƿ������֣�ץȡ���� *���ַ�* �� *�·�* ����Ϣ�����ֹ�����Щ��װ�� **88ƽ��** �� **3��2��** �׸�ֻҪ `29` ��ƽ�� `1.1`��/ƽ��

![](https://img2018.cnblogs.com/blog/996148/201811/996148-20181110171003758-723109818.png)

# �鿴������Ϣ

�����õ��ǻ�������32.0��� `firebug` �� `httpfox` ʹ�ã����� `python3` ������ǰ�ڲ��裺

>1. ���ȴ� `firefox` ������������ҳ���е���ʷ��¼������Ϊ�˷�ֹ��ǰ�� `Cookie` Ӱ����������ص����ݡ�
>2. `F12` �� `firebug` �����������ֻ�����ҳ[https://m.lianjia.com](https://m.lianjia.com)����� **����** -> **ͷ��Ϣ** ���鿴�����ͷ����Ϣ��

![](https://img2018.cnblogs.com/blog/996148/201811/996148-20181110171723996-195699230.png)

��������ͷ��Ϣ���£�����Ǻ���Ҫģ��ģ�

```
Host: m.lianjia.com
User-Agent: Mozilla/5.0 (Windows NT 6.3; WOW64; rv:32.0) Gecko/20100101 Firefox/32.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-cn,zh;q=0.8,en-us;q=0.5,en;q=0.3
Accept-Encoding: gzip, deflate
Connection: keep-alive
```

# �鿴��������

��� `firebug` �Ĳ鿴Ԫ�ؼ�ͷ��ѡ�е����鿴Ԫ�أ�

![](https://img2018.cnblogs.com/blog/996148/201811/996148-20181110172457074-30448820.png)

���ֵ�������Ҫ���� `class=inner post_ulog` �ĳ�����Ԫ�� `a` ���棬������ `BeautifulSoup` ץȡ���ƺ� `href` �ͺã�������һ���ֵ䣺

```
# ��ȡ����Ƶ��
def getChannel(html):
    channelDict = {}
    soup = BeautifulSoup(html, "html.parser")
    channels = soup.find_all("a", attrs={"class": "inner post_ulog"})
    for channel in channels:
        list_tmp = channel.find_all("div", attrs={"class": "name"})
        channelName = list_tmp[0].get_text()
        channelHref = channel.get('href')
        channelDict[channelName] = channelHref
    return channelDict
```

������£�

```
{'����': '/i/', '����': '/bj/yezhu/', '�·�': '/bj/loupan/fang/', '��С��': '/bj/xiaoqu/', '��ɽ�': '/bj/chengjiao/', '�ⷿ': '/chuzu/bj/zufang/', '���ַ�': '/bj/ershoufang/index/', 'д��¥': 'https://shang.lianjia.com/bj/'}
```

# ��ȡ���б���

���ҳ����ڰ�ť����ȡ���б��룺

![](https://img2018.cnblogs.com/blog/996148/201811/996148-20181110174515650-1279220219.png)

���ֳ��еı�����Ҫ�� `class=block city_block` �� `div` ���棬����ץȡ���оͺã�������Ҫ���ǹ��ݣ����ݵĳ��б����� `gz` ��

```
# ��ȡ���ж�Ӧ����д
def getCity(html):
    cityDict = {}
    soup = BeautifulSoup(html, "html.parser")
    citys = soup.find_all("div", attrs={"class": "city_block"})
    for city in citys:
        list_tmp = city.find_all('a')
        for a in list_tmp:
            cityHref = a.get('href')
            cityName = a.get_text()
            cityDict[cityName] = cityHref

    return cityDict
```

������£�

```
{'�Ĳ�': '/wc/', '����': '/dali/', '����': '/weihai/', '����': '/dazhou/', '��ɽ': '/zs/', '��ɽ': '/fs/', '���ͺ���': '/hhht/', '�Ϸ�': '/hf/', '�ϲ�': '/nc/', '����': '/km/', '����': '/da/', '�˲�': '/yichang/', '����': '/xy/', '����': '/jx/', '����': '/xm/', '�ൺ': '/qd/', '����': '/zhuzhou/', '����': '/xa/', 'Ȫ��': '/quanzhou/', '����': '/jn/', '����': '/cm/', 'Ϋ��': '/wf/', '����': '/bd/', '����': '/mianyang/', '����': '/cq/', '����': '/dz/', '�ϳ�': '/nanchong/', '�Ͼ�': '/nj/', '����': '/bj/', '����': '/hz/', '����': '/cz/', '����': '/xn/', '��': '/qh/', '����': '/luoyang/', '����': '/sx/', '�ȷ�': '/lf/', '����': '/hui/', '��ͨ': '/nt/', '����': '/sr/', 'տ��': '/zhanjiang/', '�ػʵ�': '/qhd/', '��ʯ': '/huangshi/', '�人': '/wh/', '���': '/tj/', '������': '/hrb/', '�Ƹ�': '/hg/', '����': '/ly/', '����': '/cc/', '�麣': '/zh/', '��̨': '/xt/', '����': '/san/', '����': '/bh/', '̫ԭ': '/ty/', '����': '/dy/', '����': '/wn/', '�е�': '/chengde/', '��ָɽ': '/wzs/', '��ˮ': '/ls/', '�ɶ�': '/cd/', '����': '/sz/', '����': '/xianyang/', '��̨': '/yt/', '��ݸ': '/dg/', '��Զ': '/qy/', '��˫����': '/xsbn/', '֣��': '/zz/', '����': '/ha/', '����': '/zhangzhou/', '����': '/changde/', '����': '/hd/', '�Ϻ�': '/sh/', '����': '/kf/', '����': '/su/', '��ˮ': '/hs/', '����': '/wx/', '����': '/gz/', '����': '/yinchuan/', '����': '/xz/', '����': '/dl/', '����': '/hk/', '����': '/jz/', '����': '/fz/', '����': '/xinxiang/', '����': '/sy/', '����': '/qz/', '�ֶ�': '/ld/', '�Ͳ�': '/zb/', 'üɽ': '/ms/', '����': '/nb/', '�żҿ�': '/zjk/', '��ͤ': '/bt/', '��ɳ': '/cs/', '�ٸ�': '/lg/', 'ʯ��ׯ': '/sjz/', '���': '/xc/', '��': '/zj/', '��ɽ': '/leshan/', '����': '/gy/'}
```

# ģ��������ַ�

������ַ����ӽ�����ַ��б�ҳ�棬�����б�ҳ��� `url` �� [https://m.lianjia.com/bj/ershoufang/index/](https://m.lianjia.com/bj/ershoufang/index/) ������ҳ���������з�ҳ��������һҳ�� `url` ����Ϊ��

![](https://img2018.cnblogs.com/blog/996148/201812/996148-20181214173524035-1048565590.png)

ֻ����ԭ������ַ���������ҳ�� `pg1` �������� `httpfox` ���澪��ķ�����һ�� `json`��

![](https://img2018.cnblogs.com/blog/996148/201812/996148-20181214175853377-417435072.png)

* ��������ĸ�λ�����и��Ҹ棺��ץȡjson��ץȡjson��*   `json` ��һ�� `API` �ӿڣ��������ҳ��˵����Ƶ�ʵͣ���ҳ�ܹ������׻��������� `API` �ӿ�һ�㲻�ỻ�����һ�����ά���ĳɱ�����ҳ�͡����룬�ӿ�ֻ��һ�� `dict` ���������ֻҪ�ڴ�������� `key` �ͺ��ˣ�����ҳ���º���Ҫ�ĵ��� `bs4` �����Ԫ�أ������Ժ󿪷������������˵��ά���ر��鷳��

���Զ�������϶���ץȡ `json`���鿴ͷ����

![](https://img2018.cnblogs.com/blog/996148/201812/996148-20181214175946299-1410954309.png)

ͷ����ҪЯ�� `cookie` ��

����������ҪЯ�� `cookie`���� `requests` �������ץȡЯ�� `cookie` ��д������ô���߾��ڴӻ�ȡ�������ӡ����б��붼��ȡ���� `cookie`������ÿһ�� `requests` �����ʱ�򣬷��� `cookie` �Ĵ���Ϊ��

```
session.get(url, headers=headers)
html_set_cookie = requests.utils.dict_from_cookiejar(session.cookies)
```

��ô�ڵ������ӡ����б����ʱ�򣬲�����������ҳ�� `html` �����෵��һ�� `cookie` ��

```
print("�������б���url")
url_get_city = url_ori + "/city/"
print("��ȡ���б���", "��", url_get_city)
html_set_cookie, html_city = getHtml(url_get_city)
cityDict = getCity(html_city)
url_city = url_ori + cityDict[city]
print("���ʻ�ȡ����", "��", url_city)
html_set_cookie, html_city_content = getHtml(url_city, _cookie=html_set_cookie)
```

Ȼ��������ͷЯ�� `cookie` ��

```
# ������ҳ
def getHtml(url, _cookie=None):
    html_bytes = session.get(url, headers=headers, cookies=_cookie)
    html_set_cookie = requests.utils.dict_from_cookiejar(session.cookies)
    return html_set_cookie, html_bytes.content.decode("utf-8", "ignore")
```

����Ҳģ������ͷЯ�� `cookie` ��ץȡ������ `json` Ϊ��

![](https://img2018.cnblogs.com/blog/996148/201812/996148-20181214181732954-1694153027.png)

����Ҫ����Ϣ�� `body` ���棬ֱ�ӽ��� `html` ��� `dict` ����ȡ `body` ������

```
html_bytes = session.get(url_detail, headers=headerJson, cookies=html_set_cookie)
html_detail = html_bytes.content.decode("utf-8", "ignore")
detailJson = json.loads(html_detail)
```

������Ϣ���� `class=item_list` ���棬ֱ���� `bs4` ץȡ���ɡ�����ץȡ������ϢΪ�����⡢��ǩ�����ӹ��졢������ܼۡ����ۡ����ݳ�������ҳ `url` �ȣ�

![](https://img2018.cnblogs.com/blog/996148/201812/996148-20181214181849583-1278850976.png)

��ȡ��Ϣ�Ĳ��ִ���Ϊ��

```
# ��ȡ���ַ�����ϸ��Ϣ
def getInfoErshoufang(html):
    detailArr = []

    soup = BeautifulSoup(html, "html.parser")
    detailInfo = soup.find_all("div", attrs={"class": "item_list"})
    detailUrl = soup.find_all("a", attrs={"class": "a_mask"})
    details = zip(detailInfo, detailUrl)
    for info_url in details:
        info = info_url[0]
        detailDict = {}
        # ��ȡ����
        title_tmp = info.find_all("div", attrs={"class": "item_main"})
        detail_title = title_tmp[0].get_text()
        # ��ȡ���ݴ�С
        size_tmp = info.find_all("div", attrs={"class": "item_other"})
        detail_size = size_tmp[0].get_text()
        # ��ȡ�۸񵥼�
        price_total_tmp = info.find_all("span", attrs={"class": "price_total"})
        detail_price_total = price_total_tmp[0].get_text()
        try:
            unit_price_tmp = info.find_all("span", attrs={"class": "unit_price"})
            detail_unit_price = unit_price_tmp[0].get_text()
        except:
            detail_unit_price = "88888888Ԫ/ƽ"
        # ��ȡ��ǩ
        tag_tmp = info.find_all("div", attrs={"class": "tag_box"})
        detail_tag = tag_tmp[0].get_text()
        # ��ȡ����ҳ
        url_a = info_url[1]
```

# ��װ����

Ϊ���ô�����ӵĺ�г������Դ�������˷�װ���������¼������棺

>1. ѡ�����
>2. ѡ��鿴���ַ����·���
>3. ����ҳץȡҳ��
>4. �����׸�
>5. �����׸���������

Ŀǰֻд��ô���ˣ��Ͼ�����ֻ�̷��������ߣ�����ץȡ����Ϣ��Ҫ��λ���߸����Լ����������

# ����Դ��

�����Ѿ���Դ��ŵ� `github` �����ˣ����� `3` �� `py` �ļ���

>1. lianjia.py ����תҳ�浽����ҳ�Ĵ��룬Ϊ������
>2. GetDetail.py��ץȡ����ҳ��ҳ�Ĵ���
>3. GetInfo.py����ȡ����ҳ������Ϣ�Ĵ���