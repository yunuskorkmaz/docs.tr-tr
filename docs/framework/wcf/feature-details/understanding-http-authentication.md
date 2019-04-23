---
title: HTTP Kimlik Doğrulamasını Anlama
ms.date: 03/30/2017
ms.assetid: 9376309a-39e3-4819-b47b-a73982b57620
ms.openlocfilehash: 430b0ddb98514b605178124f331e5152605a2b89
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206401"
---
# <a name="understanding-http-authentication"></a>HTTP Kimlik Doğrulamasını Anlama
Kimlik doğrulaması, bir istemcinin bir kaynağa erişmek uygun olup olmadığını belirleme işlemi şeklindedir. HTTP protokolü anlaşması güvenli kaynak erişimi için bir araç olarak kimlik doğrulamasını destekler.  
  
 İstemciden gelen ilk istek, genellikle tüm kimlik doğrulama bilgilerini içermeyen bir anonim istek değildir. HTTP sunucu uygulamaları, söz konusu kimlik doğrulamasını gösteren çalışırken anonim istek gereklidir reddedebilirsiniz. Sunucu uygulaması, desteklenen kimlik doğrulama şemasını göstermek için WWW kimlik doğrulama üst bilgileri gönderir. Bu belge, çeşitli kimlik doğrulama düzeni için HTTP açıklar ve Windows Communication Foundation (WCF) destek açıklanır.  
  
## <a name="http-authentication-schemes"></a>HTTP kimlik doğrulama şeması  
 Sunucu, aralarından seçim yapabileceğiniz istemcisi için birden çok kimlik doğrulama düzeni belirtebilirsiniz. Aşağıdaki tabloda Windows uygulamalarında yaygın olarak bulunan kimlik doğrulama düzenleri bazılarını açıklar.  
  
|Kimlik doğrulama düzeni|Açıklama|  
|---------------------------|-----------------|  
|Anonim|Bir anonim istek tüm kimlik doğrulama bilgilerini içermiyor. Bunun eşdeğeri olan kaynağa erişim herkesin izni verme.|  
|Temel|Temel kimlik doğrulaması için istemci kullanıcı adı ve parola içeren bir Base64 ile kodlanmış dize gönderir. Base64 şifreleme bir biçimde değil ve aynı kullanıcı adı ve parola düz metin olarak gönderme olarak düşünülmelidir. Bir kaynak korunması gereken kesin temel kimlik doğrulaması dışındaki bir kimlik doğrulama düzeni kullanmayı düşünün.|  
|Özet|Özet kimlik doğrulaması temel kimlik doğrulaması değiştirmeye yönelik bir sınama yanıtı düzenidir. Sunucu, bir dize olarak adlandırılan rastgele veri gönderir. bir *nonce* istemciye bir karşılıklı olarak. İstemci, kullanıcı adı, parola ve ek bilgiler arasında nonce içeren karma ile yanıt verir. Bu exchange tanıtır karmaşıklığı ve verilerin karması bu kimlik doğrulama düzeni ile kullanıcının kimlik bilgilerini çalıp daha zor hale getirir.<br /><br /> Özet kimlik doğrulaması, Windows etki alanı hesaplarının kullanılmasını gerektirir. Özet *bölge* Windows etki alanı adıdır. Bu nedenle, Windows gibi etki alanları Windows XP Home Edition, Özet kimlik doğrulaması ile desteklemeyen bir işletim sistemini çalıştıran bir sunucu kullanamazsınız. Buna karşılık, istemci, Windows etki alanları desteklemeyen bir işletim sisteminde çalıştığında, bir etki alanı hesabı açıkça kimlik doğrulaması sırasında belirtilmelidir.|  
|NTLM|NT LAN Manager (NTLM) kimlik doğrulamasını, Özet kimlik doğrulaması securer çeşididir bir sınama yanıtı düzenidir. NTLM, kodlanmamış kullanıcı adı ve parola yerine sınama verileri dönüştürmek için Windows kimlik bilgilerini kullanır. NTLM kimlik doğrulaması, istemci ve sunucu arasında birden çok değişimleri gerektirir. Sunucu ve tüm müdahil proxy'leri başarılı kimlik doğrulamalarını tamamlamak için kalıcı bağlantılar desteklemesi gerekir.|  
|Anlaşma|Anlaşma kimlik doğrulama durumuna bağlı olarak NTLM kimlik doğrulaması ve Kerberos protokolü arasında otomatik olarak seçer. Varsa Kerberos protokolü kullanılır; Aksi takdirde, NTLM denenir. Kerberos kimlik doğrulaması, NTLM üzerinde önemli ölçüde artırır. Kerberos kimlik doğrulaması, hem de NTLM daha hızlıdır ve karşılıklı kimlik doğrulaması ve kimlik bilgilerini uzak makinelere temsili sağlar.|  
|Windows Live ID|Temel alınan Windows HTTP hizmet Federasyon protokollerini kullanarak kimlik doğrulaması içerir. Ancak, standart HTTP taşımaları wcf'de gibi Microsoft Windows Live ID, Federasyon kimlik doğrulama düzenleri kullanımını desteklemez Bu özellik için destek, kullanılarak ileti güvenliği şu anda kullanılabilir. Daha fazla bilgi için [Federasyon ve verilen belirteçler](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).|  
  
## <a name="choosing-an-authentication-scheme"></a>Bir kimlik doğrulama düzeni seçme  
 Olası kimlik doğrulama düzeni için HTTP sunucusu seçerken dikkate alınması gereken birkaç öğe şunları içerir:  
  
-   Kaynak korunması gerekip gerekmediğini düşünün. HTTP kimlik doğrulaması kullanarak daha fazla veri aktarımı gerektirir ve istemciler ile birlikte çalışabilirlik sınırlayabilirsiniz. Korunması gerekmez kaynakları anonim erişime izin verin.  
  
-   Kaynak korunması gerekiyorsa, hangi kimlik doğrulama düzenleri gerekli düzeyde güvenlik sağladığını göz önünde bulundurun. Burada tartışılan zayıf standart kimlik doğrulama düzeni, temel kimlik doğrulaması kullanılır. Temel kimlik doğrulaması, kullanıcının kimlik bilgilerini korumaz. En güçlü standart kimlik doğrulama Anlaşma kimlik doğrulaması, Kerberos protokolü kaynaklanan kullanılır.  
  
-   Bir sunucu (WWW kimlik denetimi üst bilgilerinde) herhangi sunmalıdır değil değil Düzen hazır kabul etmek ya da, yeterince korumalı kaynağa güvenliğini sağlamaz. İstemciler sunucusu kimlik doğrulama düzeni arasında seçim ücretsizdir. Bazı istemciler varsayılan bir zayıf bir kimlik doğrulama düzeni ya da sunucu listesindeki ilk kimlik doğrulaması düzeni.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Aktarım Güvenliğine Genel Bakış](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)
- [Aktarım Güvenliği ile Kimliğe Bürünme Kullanma](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md)
- [Temsilcilik ve Kimliğe Bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
