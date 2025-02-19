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
