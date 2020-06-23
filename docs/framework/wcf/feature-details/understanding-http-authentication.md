---
title: HTTP Kimlik Doğrulamasını Anlama
description: HTTP kimlik doğrulama şemaları ve bir kimlik doğrulama düzeni seçmek dahil olmak üzere WCF 'de HTTP kimlik doğrulamasına giriş konusunu gözden geçirin.
ms.date: 03/30/2017
ms.assetid: 9376309a-39e3-4819-b47b-a73982b57620
ms.openlocfilehash: 761ab7a92aa26ce1437eefa360e5b46df179e32d
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246525"
---
# <a name="understanding-http-authentication"></a>HTTP Kimlik Doğrulamasını Anlama
Kimlik doğrulaması, bir istemcinin bir kaynağa erişmeye uygun olup olmadığını belirleme işlemidir. HTTP protokolü, güvenli bir kaynağa erişim anlaşması için bir yol olarak kimlik doğrulamasını destekler.  
  
 İstemciden gelen ilk istek, herhangi bir kimlik doğrulama bilgisi içermeyen, genellikle anonim bir istek olur. HTTP sunucusu uygulamaları, kimlik doğrulamasının gerekli olduğunu belirten anonim isteği reddedebilir. Sunucu uygulaması, desteklenen kimlik doğrulama düzenlerini belirtmek için WWW-Authentication üst bilgilerini gönderir. Bu belge, HTTP için çeşitli kimlik doğrulama düzenlerini açıklar ve Windows Communication Foundation (WCF) desteğini açıklar.  
  
## <a name="http-authentication-schemes"></a>HTTP kimlik doğrulama şemaları  
 Sunucu, istemcinin arasından seçim yapmak için birden çok kimlik doğrulama düzeni belirtebilir. Aşağıdaki tabloda, Windows uygulamalarında yaygın olarak bulunan bazı kimlik doğrulama düzenleri açıklanmaktadır.  
  
|Kimlik doğrulama düzeni|Description|  
|---------------------------|-----------------|  
|Anonim|Anonim bir istek herhangi bir kimlik doğrulama bilgisi içermiyor. Bu, herkese kaynağa erişim izni vermeye eşdeğerdir.|  
|Temel|Temel kimlik doğrulaması, istemci için Kullanıcı adı ve parola içeren Base64 kodlamalı bir dize gönderir. Base64 bir şifreleme formu değildir ve Kullanıcı adı ve parolayı şifresiz metin olarak göndermekle aynı olarak düşünülmelidir. Bir kaynağın korunması gerekiyorsa, temel kimlik doğrulaması dışında bir kimlik doğrulama düzeni kullanmayı kesin olarak düşünün.|  
|Bilgisi|Özet kimlik doğrulaması, temel kimlik doğrulamanın yerini alacak bir sınama yanıt düzenidir. Sunucu, bir sınama olarak istemciye *nonce* adlı bir rastgele veri dizesi gönderir. İstemci, ek bilgiler arasında Kullanıcı adı, parola ve nonce içeren bir karmayla yanıt verir. Bu değişim tanıtıldığı ve veri karmaşasından bu kimlik doğrulama düzeniyle kullanıcının kimlik bilgilerini çalmak ve yeniden kullanmak daha zor hale gelir.<br /><br /> Özet kimlik doğrulaması için Windows etki alanı hesaplarının kullanılması gerekir. Özet *bölgesi* Windows etki alanı adıdır. Bu nedenle, Windows XP Home Edition gibi Windows etki alanlarını desteklemeyen bir işletim sisteminde çalıştıran bir sunucuyu Özet kimlik doğrulaması ile kullanamazsınız. Buna karşılık, istemci Windows etki alanlarını desteklemeyen bir işletim sisteminde çalıştırıldığında, kimlik doğrulaması sırasında açık bir etki alanı hesabı belirtilmelidir.|  
|NTLM|NT LAN Manager (NTLM) kimlik doğrulaması, Özet kimlik doğrulamasının Securer çeşitlemesi olan bir sınama yanıt şemadır. NTLM, kodlanmış Kullanıcı adı ve parola yerine, sınama verilerini dönüştürmek için Windows kimlik bilgilerini kullanır. NTLM kimlik doğrulaması, istemci ve sunucu arasında birden çok değişim gerektirir. Sunucu ve aradaki tüm proxy 'ler, kimlik doğrulamasını başarıyla tamamlamaya yönelik kalıcı bağlantıları desteklemelidir.|  
|Anlaşma|Negotiate kimlik doğrulaması, kullanılabilirliğine bağlı olarak Kerberos protokolü ve NTLM kimlik doğrulaması arasında otomatik olarak seçilir. Kullanılabilir olduğunda Kerberos protokolü kullanılır; Aksi takdirde, NTLM denenir. Kerberos kimlik doğrulaması, NTLM üzerinde önemli ölçüde gelişir. Kerberos kimlik doğrulaması, NTLM 'den daha hızlıdır ve uzak makinelerde kimlik bilgilerinin karşılıklı kimlik doğrulaması ve temsilciliğini kullanılmasına izin verir.|  
|Windows Live ID|Temel alınan Windows HTTP hizmeti, Federasyon protokollerini kullanarak kimlik doğrulaması içerir. Ancak, WCF 'deki standart HTTP aktarımları, Microsoft Windows Live ID gibi federal kimlik doğrulama şemaları kullanımını desteklemez. Bu özellik için destek, şu anda ileti güvenliği kullanılarak sunulmaktadır. Daha fazla bilgi için bkz. [Federasyon ve verilen belirteçler](federation-and-issued-tokens.md).|  
  
## <a name="choosing-an-authentication-scheme"></a>Kimlik doğrulama düzeni seçme  
 Bir HTTP sunucusu için olası kimlik doğrulama düzenlerini seçerken, dikkate alınması gereken birkaç öğe şunlardır:  
  
- Kaynağın korunması gerekip gerekmediğini göz önünde bulundurun. HTTP kimlik doğrulamasının kullanılması, daha fazla veri iletilmesi gerektirir ve istemcilerle birlikte çalışabilirliği sınırlayabilir. Korunması gerekmeyen kaynaklara anonim erişime izin verin.  
  
- Kaynağın korunması gerekiyorsa, hangi kimlik doğrulama düzenlerinin gerekli güvenlik düzeyini sağlamasını düşünün. Burada ele alınan en zayıf standart kimlik doğrulama şeması, temel kimlik doğrulamadır. Temel kimlik doğrulaması, kullanıcının kimlik bilgilerini korumaz. En güçlü standart kimlik doğrulama şeması, Negotiate kimlik doğrulamadır ve Kerberos protokolüne yol açar.  
  
- Bir sunucu, kabul etmek için hazırlanmadığı veya korunan kaynağı yeterince güvenli hale desteklemediği herhangi bir düzen (WWW-Authentication üst bilgilerinde) sunmamalıdır. İstemciler, sunucunun sunduğu herhangi bir kimlik doğrulama şeması arasından seçim yapmak için ücretsizdir. Bazı istemciler, zayıf bir kimlik doğrulama şemasına veya sunucu listesindeki ilk kimlik doğrulama şemasına varsayılan olarak verilebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Aktarım Güvenliğine Genel Bakış](transport-security-overview.md)
- [Taşıma Güvenliği ile Kimliğe Bürünme Kullanma](using-impersonation-with-transport-security.md)
- [Temsilcilik ve Kimliğe Bürünme](delegation-and-impersonation-with-wcf.md)
