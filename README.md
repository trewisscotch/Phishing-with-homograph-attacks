# Phishing-with-homograph-attacks
<p align="center">
  <img src="https://github.com/trewisscotch/Phishing-with-homograph-attacks/blob/main/apple.com_.png" alt="animated" />
</p>
What the attacker needs is to be able to register a site where the address is written differently, but looks the same to the user, and that is why homograph attacks are used.
This example is a part of a proof of concept carried out by the researcher Xudong Zheng, who registered the domain https://www.xn--80ak6aa92e.com/. You can see how it works by visiting the link through the Firefox browser.

What makes it possible is the use of Unicode characters from non-Latin writing systems, like Cyrillic or Greek. In these alphabets we can find characters that are similar, or even identical to those we use in the Latin alphabet and in URLs. Thanks to Punycode, which is a coding syntax that allows any Unicode character to be translated into a more limited string of characters that is compatible with URLs, a domain using these characters can be registered.

For example, it is possible to register a domain name such as “xn--pple-43d.com,” which is interpreted by the browser as “apple.com,” but is actually written using the Cyrillic character “а” (U+0430) instead of the ASCII “a” (U+0041). While both characters look the same to the naked eye, for the purpose of browsers and security certificates these are two different characters, and so represent different domains.

There are numerous examples, like “tωitter.com” (xn--titter-i2e.com in Punycode) and “gmạil.com” (xn--gmil-6q5a.com). You can even have fun creating your own combinations with a Unicode to Punycode converter.

Many current browsers have systems that try to prevent these types of attacks. For instance, in Firefox or Chrome, if a domain contains characters from different writing systems, rather than showing its Unicode form, they show the corresponding Punycode.

So, in the previous examples, instead of seeing “apple.com” (Unicode form), we would see “xn--pple-43d.com” (Punycode form), while “tωitter.com” would be “xn--titter-i2e.com.”

Nevertheless, in the proof of concept, Xudong Zheng manages to sidestep this protection by registering the domain “apple.com” using only characters from the Cyrillic alphabet. This way, “xn--80ak6aa92e.com” looks like аррӏе.com.

The researcher also went one step further, using Amazon to obtain a TLS certificate for his domain, which at first glance is quite convincing:
<p align="center">
  <img src="https://github.com/trewisscotch/Phishing-with-homograph-attacks/blob/main/apple.com-certificado.png" alt="animated" />
</p>
But if we go in and look at the details, we can see that it actually belongs to “xn--80ak6aa92e.com:”
<p align="center">
  <img src="https://github.com/trewisscotch/Phishing-with-homograph-attacks/blob/main/certificado.png" alt="animated" />
</p>
While this vulnerability has now been corrected in the latest versions of Chrome and Internet Explorer, other browsers like Firefox still suffer from this problem. An alternative in Firefox is to set the option network.IDN_show_punycode as true, so that it always shows characters in their Punycode form.
Even so, the gmạil.com site from the previous example also manages to evade Chrome’s protection, as it only uses Latin characters, but includes a special Latin character (“ạ”—note the dot below the “a”), which is displayed by the browser.

## DEVELOPER DO NOT SUPPORT ANY OF THE ILLEGAL ACTIVITIES.
## Contact Me on telegram or twitter: https://twitter.com/TrewisScotch / https://t.me/HiroSCOTCH#
