# Summernote-xss-protected
Summernote is a super simple JavaScript library that helps you create WYSIWYG editors online. Home page: https://summernote.org

Summernote has the Cross Site Scripting vulnerability over almost over 2 years by now.

Affected versions of this package are vulnerable to Cross-site Scripting (XSS). It is possible to inject JavaScript with object decoding such as <code class="notranslate">&lt;script&gt;alert(1)&lt;/script&gt;</code> resulting in XSS. The fix is to sanitize the input on the package before further processing/executing.

Issue: [#3782](https://github.com/summernote/summernote/pull/3782).

This fix made by me directly in summernote-lite.js version v8.20, because the problem is going on in summernote core js and not possible to create protection as a module, it protects adding bad urls into "add link", "image", and "media url", same function can be use for "onPaste" calback to clean all html codes in pasted content.

Will be released on [Askbrn.com](https://askbrn.com) as soon as I am done with the site.
