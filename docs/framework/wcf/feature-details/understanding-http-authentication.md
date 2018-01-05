---
title: "HTTP Kimlik Doğrulamasını Anlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9376309a-39e3-4819-b47b-a73982b57620
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 32d7df95c6acbe34a677cbd2951fd912466d015f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="understanding-http-authentication"></a>HTTP Kimlik Doğrulamasını Anlama
Kimlik doğrulaması bir istemci bir kaynağa erişmek uygun olup olmadığını belirleme işlemidir. Güvenli bir kaynağa erişim anlaşmak için bir araç olarak kimlik doğrulaması HTTP protokolünü destekler.  
  
 İstemciden gelen ilk istek, herhangi bir kimlik doğrulama bilgi içermeyen bir anonim istek genellikle değildir. HTTP sunucu uygulamaları belirten bu kimlik doğrulama sırasında anonim istek gereklidir reddedebilirsiniz. Sunucu uygulaması desteklenen kimlik doğrulama şemasını belirtmek için WWW-kimlik doğrulama üstbilgileri gönderir. Bu belge çeşitli kimlik doğrulama şemasını için HTTP ve bunların desteği anlatılmaktadır [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
## <a name="http-authentication-schemes"></a>HTTP kimlik doğrulaması düzeni  
 Sunucu aralarından seçim yapabileceğiniz istemci için birden çok kimlik doğrulama düzeni belirtebilirsiniz. Aşağıdaki tabloda Windows uygulamalarında yaygın olarak bulunan kimlik doğrulama şemasını bazıları açıklanmaktadır.  
  
|Kimlik doğrulama şeması|Açıklama|  
|---------------------------|-----------------|  
|Anonim|Anonim İstek herhangi bir kimlik doğrulama bilgi içermiyor. Bu eşdeğer olan herkes verme kaynağa erişim.|  
|Temel|Temel kimlik doğrulaması için istemci kullanıcı adı ve parola içeren Base64 ile kodlanmış bir dize gönderir. Base64 şifreleme bir biçimde değil ve aynı kullanıcı adı ve parola düz metin olarak gönderme olarak düşünülmelidir. Güçlü bir kaynak korunması gerekiyorsa, temel kimlik doğrulaması dışında bir kimlik doğrulama düzeni kullanmayı düşünün.|  
|Özet|Özet kimlik doğrulaması temel kimlik doğrulaması değiştirmeye yönelik bir sınama yanıtı düzenidir. Sunucu adı verilen rastgele veri dizesi gönderir bir *nonce* istemciye bir karşılıklı olarak. İstemci kullanıcı adı, parola ve ek bilgiler arasında nonce içeren bir karma ile yanıt verir. Bu exchange tanıtır karmaşıklığı ve veri karma çalabilir ve bu kimlik doğrulama düzeni ile kullanıcının kimlik bilgilerini yeniden daha zor hale.<br /><br /> Özet kimlik doğrulaması Windows etki alanı hesapları kullanılmasını gerektirir. Özet *bölge* Windows etki alanı adıdır. Bu nedenle, Windows etki alanlarında, Windows XP Home Edition gibi Özet kimlik doğrulaması ile desteklemeyen bir işletim sistemi çalıştıran bir sunucuya kullanamazsınız. Buna karşılık, istemci, Windows etki alanlarında desteklemeyen bir işletim sisteminde çalıştığında, bir etki alanı hesabı açıkça kimlik doğrulaması sırasında belirtilmelidir.|  
|NTLM|NT LAN Yöneticisi (NTLM) kimlik doğrulaması Özet kimlik doğrulaması securer çeşididir bir sınama yanıtı düzenidir. NTLM kodlanmamış kullanıcı adı ve parola yerine Çekişme verileri dönüştürmek için Windows kimlik bilgilerini kullanır. NTLM kimlik doğrulaması istemci ve sunucu arasında birden çok alışverişleri gerektirir. Sunucu ve müdahalede bulunan proxy'ler başarıyla kimlik doğrulamasını tamamlamak için kalıcı bağlantılar desteklemesi gerekir.|  
|Anlaşma|Anlaşma kimlik doğrulaması kullanılabilirlik bağlı olarak NTLM kimlik doğrulaması ve Kerberos protokolü arasında otomatik olarak seçer. Varsa Kerberos protokolü kullanılır; Aksi takdirde, NTLM denenir. Kerberos kimlik doğrulaması, NTLM üzerinde önemli ölçüde iyileştirir. Kerberos kimlik doğrulaması hem NTLM daha hızlıdır ve karşılıklı kimlik doğrulaması kullanımını ve uzak makineleri kimlik bilgilerinin Devredilmesine izin verir.|  
|Windows Live ID|Temel alınan Windows HTTP hizmeti, federe protokollerini kullanarak kimlik doğrulaması içerir. Ancak, standart HTTP taşımaları [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Microsoft Windows Live ID gibi federe kimlik doğrulama şemasını kullanımını desteklemez Bu özellik için destek kullanımı ile ileti güvenliği şu anda kullanılamıyor. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Federasyon ve verilen belirteçleri](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).|  
  
## <a name="choosing-an-authentication-scheme"></a>Bir kimlik doğrulama düzeni seçme  
 Bir HTTP sunucusu için olası kimlik doğrulama şemasını seçerken, dikkate alınması gereken birkaç öğeler aşağıdakileri içerir:  
  
-   Kaynak korunacak gerekip gerekmediğini düşünün. HTTP kimlik doğrulaması kullanarak daha fazla veri aktarırken gerektirir ve birlikte çalışabilirlik istemcileriyle sınırlayabilir. Korunması gerekmez kaynakları anonim erişime izin ver.  
  
-   Kaynak korunması gerekiyorsa, hangi kimlik doğrulama şemasını gerekli güvenlik düzeyini sağlamak göz önünde bulundurun. Burada tartışılan zayıf standart kimlik doğrulama düzeni, temel kimlik doğrulaması kullanılır. Temel kimlik doğrulaması kullanıcının kimlik bilgilerini korumaz. Güçlü standart kimlik doğrulama şemasını Anlaşma kimlik doğrulaması, Kerberos protokolü kaynaklanan kullanılır.  
  
-   Bir sunucu (WWW kimlik doğrulaması üstbilgilerinde) herhangi sunmalıdır değil değil düzeni hazırlanmış kabul etmek veya yeterli korumalı kaynağa güvenli değil. İstemciler sunucu sunar kimlik doğrulama şemasını arasında seçim boş. Bazı istemciler varsayılan zayıf bir kimlik doğrulama düzeni veya sunucunun listesindeki ilk kimlik doğrulama düzeni.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Aktarım Güvenliğine Genel Bakış](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 [Aktarım Güvenliği ile Kimliğe Bürünme Kullanma](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md)  
 [Temsilcilik ve Kimliğe Bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
