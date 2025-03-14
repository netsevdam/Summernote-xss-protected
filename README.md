# Summernote-xss-protected
Summernote is a super simple JavaScript library that helps you create WYSIWYG editors online. Home page: https://summernote.org

Summernote has the Cross Site Scripting vulnerability over almost over 2 years by now. can be tested on main site here https://summernote.org by inserting codes bellow as link, image, media url, and in codeview.

<code class="notranslate">&lt;b onmouseover=alert('Wufff!')&gt;click me!&lt;/b&gt;</code>

onerror
<code class="notranslate">&lt;img src="http://url.to.file.which/not.exist" onerror=alert(document.cookie);&gt;</code>


All versions are vulnerable to Cross-site Scripting (XSS). It is possible to inject JavaScript with object decoding such as <code class="notranslate">&lt;script&gt;alert(1)&lt;/script&gt;</code> resulting in XSS. The fix is to sanitize the input on the package before further processing/executing.

Issue: [#3782](https://github.com/summernote/summernote/pull/3782).

This fixed directly in summernote-lite.js version v8.20, because the problem is going on in summernote core js and not possible to create protection as a module, it protects adding bad urls into "add link", "image", "media url" and "codeview", same function can be use for "onPaste" calback to clean all html codes in pasted content.
Codes inserted in codeview will be deleted just text allowed, so be carefull to write all the way down the post in editor and then preview in codeview, it will remove all html tags exclude text.
That function needs a better regepx to keep allowed html tags, I am not familier with summernote. So what I did was just for my own needs.

I create a new function to remove bad protocols from the editor codeview, link, image and media url, I activated alert when inserting a none acceptable protocol as a link, you can remove it.

I added created function on the top of the summernote-lite.js so anyone can see the function at the top of all codes and click on function name to see what and where are the changes, I tried to replace html entities but the function keep added entities.
I had that much knowledge and did what I could do, so if you know better share with us and make it better.

Important : This fix is safe to use but in case you need to do filters, using this file is on your own risk.

I will let know the creators of the summernote, that guys will do good job and go way further. "http://" removed and added "//" to allowed protocol so it can support http or https in case user didin't select use protocols etc..

Demo can be seen on here https://koctaksi.com/ removed
[Mavi Taksi Blog](https://mavitaksi.blogspot.com/),
[1Kamp Korsan Taksi](https://1kamp.com/istanbul-korsan-taksi/),
[İstanbul Korsan Taksi](https://istanbul-korsan-taksi.renderforestsites.com/),
[Mavi Taksi İstanbul](https://mavitaksiist.wixsite.com/istanbul-ulasim),
[İstanbul Korsan Taksi Rehberi](https://sites.google.com/view/istanbulkorsantaksirehberi/),
[Hemen Kredi](https://hemenkredi.org/),
[Mavi Taksi](https://mavitaksi.com/),
[Korsan Taksi İstanbul](https://korsantaksiistanbul.com/),
[Koç Taksi](https://koctaksi.com),
[Esenyurt Korsan Taksi](https://esenyurtkorsantaksici.blog),
[Bursa Korsan Taksi](https://mavitaksi.com/bursa-korsan-taksi),
[Tekirdağ Korsan Taksi](https://mavitaksi.com/tekirdag-korsan-taksi),
[Sakarya Korsan Taksi](https://mavitaksi.com/sakarya-korsan-taksi),
[Bursa Korsan Taksi - Korsan Taksi İstanbul](https://korsantaksiistanbul.com/bursa-korsan-taksi/),
[Bursa Korsan Taksi - Mavi Taksi](https://mavitaksi.com/bursa-korsan-taksi),
[Bursa Mudanya Korsan Taksi - Koç Taksi](https://koctaksi.com/tag/bursa-mudanya-korsan-taksi/),
[Bursa Mudanya Korsan Taksi - Korsan Taksi İstanbul](https://korsantaksiistanbul.com/bursa-mudanya-korsan-taksi/),
[Bursa Mudanya Korsan Taksi - Mavi Taksi](https://mavitaksi.com/tag/bursa-mudanya-korsan-taksi),
[Bursa Orhangazi Korsan Taksi - Mavi Taksi](https://mavitaksi.com/tag/bursa-orhangazi-korsan-taksi),
[Bursa Orhangazi Korsan Taksi - Korsan Taksi İstanbul](https://korsantaksiistanbul.com/bursa-orhangazi-korsan-taksi/),
[Bursa Orhangazi Korsan Taksi - Koç Taksi](https://koctaksi.com/tag/bursa-orhangazi-korsan-taksi/),
[Bursa Yenişehir Korsan Taksi - Korsan Taksi İstanbul](https://korsantaksiistanbul.com/bursa-yenisehir-korsan-taksi/),
[Bursa Orhaneli Korsan Taksi - Korsan Taksi İstanbul](https://korsantaksiistanbul.com/bursa-orhaneli-korsan-taksi/),
[Bursa Mustafakemalpaşa Korsan Taksi - Korsan Taksi İstanbul](https://korsantaksiistanbul.com/bursa-mustafakemalpasa-korsan-taksi/),
[Bursa İnegöl Korsan Taksi - Korsan Taksi İstanbul](https://korsantaksiistanbul.com/bursa-inegol-korsan-taksi/),
[Bursa Harmancık Korsan Taksi - Korsan Taksi İstanbul](https://korsantaksiistanbul.com/bursa-harmancik-korsan-taksi/),
[İstanbul Korsan Taksi - Mavi Taksi](https://mavitaksi.com/korsan-taksi-istanbul),
[Bahçeşehir Korsan Taksi - Mavi Taksi](https://mavitaksi.com/bahcesehir-korsan-taksi-05102203075),
[Korsan Taksi - Mavi Taksi](https://mavitaksi.com/korsan-taksi),
[Beylikdüzü Korsan Taksi - Mavi Taksi](https://mavitaksi.com/beylikduzu-korsan-taksi),
[İstanbul Avrupa Yakası Korsan Taksi - Mavi Taksi](https://mavitaksi.com/istanbul-avrupa-yakasi-korsan-taksi),
[İstanbul - Bursa Korsan Taksi - Mavi Taksi](https://mavitaksi.com/istanbul-ile-bursa-arasi-korsan-taksi-05102203075),
[Sultangazi Korsan Taksi - Mavi Taksi](https://mavitaksi.com/sultangazi-korsan-taksi),
[Sabiha Gökçen - Esenyurt Korsan Taksi - Mavi Taksi](https://mavitaksi.com/sabiha-gokcen-havalimani-ndan-esenyurt-a-korsan-taksi),
[Esenyurt Korsan Taksi - Mavi Taksi](https://mavitaksi.com/korsan-taksi-esenyurt),
[Balıkyolu Korsan Taksi - Mavi Taksi](https://mavitaksi.com/balikyolu-korsan-taksi),
[Güzelyurt Korsan Taksi - Mavi Taksi](https://mavitaksi.com/guzelyurt-korsan-taksi),
[Akbatı Korsan Taksi - Mavi Taksi](https://mavitaksi.com/akbati-korsan-taksi),
[Marmara Park Korsan Taksi - Mavi Taksi](https://mavitaksi.com/marmarapark-korsan-taksi),
[Saadetdere Korsan Taksi - Mavi Taksi](https://mavitaksi.com/saadetdere-korsan-taksi),
[https://mavitaksi.com/sakarya-korsan-taksi-05102203075](https://mavitaksi.com/sakarya-korsan-taksi-05102203075),
[https://mavitaksi.com/bursa-korsan-taksi](https://mavitaksi.com/bursa-korsan-taksi),
[https://mavitaksi.com/istanbul-korsan-taksi](https://mavitaksi.com/istanbul-korsan-taksi),
[https://koctaksi.com/okmeydani-korsan-taksi/](https://koctaksi.com/okmeydani-korsan-taksi/),
