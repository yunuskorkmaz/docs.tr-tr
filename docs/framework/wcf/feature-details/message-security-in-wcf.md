---
title: WCF'de İleti Güvenliği
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a80efb59-591a-4a37-bb3c-8fffa6ca0b7d
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3ef96dd25903076fedc59ad1507674dd40dcfcc5
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="message-security-in-wcf"></a>WCF'de İleti Güvenliği
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] güvenlik sağlamak için iki ana modu vardır (`Transport` ve `Message`) ve üçüncü modu (`TransportWithMessageCredential`) iki birleştirir. Bu konuda, ileti güvenliği ve kullanmak için nedenleri açıklanmaktadır.  
  
## <a name="what-is-message-security"></a>İleti güvenlik nedir?  
 İleti güvenliği WS-Security belirtimi iletileri güvenli hale getirmek için kullanır. WS-Securityspecification gizlilik, bütünlük ve kimlik doğrulamasını (aktarım düzeyi) yerine SOAP iletisi düzeyinde emin olmak için Mesajlaşma SOAP geliştirmeler açıklanmaktadır.  
  
 Kısaca, güvenlik kimlik bilgileri ve tüm ileti koruma (imzalama veya şifreleme) yanı sıra her bir iletiyle talepleri kapsülleyerek Aktarım güvenlik ile ileti güvenliği farklıdır. Güvenlik içeriği değiştirerek doğrudan iletiye uygulama güvenli bir ileti güvenlik konuları göre otomatik olarak içeren olmasını sağlar. Bu taşıma güvenliği kullanıldığında, mümkün olmayan bazı senaryolar sağlar.  
  
## <a name="reasons-to-use-message-security"></a>İleti güvenliği kullanmanın nedeni  
 İleti düzeyi güvenlik tüm güvenlik bilgileri kapsüllenmiş ileti. Aktarım düzeyinde güvenlik yerine ileti düzeyi güvenliği ile ileti güvenliği aşağıdaki avantajlara sahiptir:  
  
-   Uçtan uca güvenlik. Noktadan noktaya iletişim olduğunda taşıma güvenliği, Güvenli Yuva Katmanı (SSL) gibi iletileri yalnızca güvenliğini sağlar. İleti ultimate alıcı ulaşmadan önce bir veya daha fazla SOAP aracılar'için (örneğin bir yönlendirici) yönlendirilir, isteğe bağlı olarak bir aracı hattan okur sonra ileti korumalı değil. Ayrıca, istemci kimlik doğrulaması bilgilerini yalnızca ilk aracı için kullanılabilir ve bant dışı şekilde ultimate alıcıya gerekirse yeniden iletilmesi gerekir. Tüm rota tek tek atlama arasında SSL güvenlik kullanıyorsa bile bu geçerlidir. İleti güvenliği doğrudan iletisiyle çalışır ve XML'de güvence altına alır çünkü ultimate alıcı erişmeden önce kaç tane dahil edilen aracılar bağımsız olarak iletiyle güvenlik kalır. Bu doğru uçtan uca güvenlik senaryo sağlar.  
  
-   Daha fazla esneklik. İletinin tamamı yerine ileti parçalarının imzalanmış veya şifrelenmiş. Başka bir deyişle, aracılar için tasarlanmıştır iletinin bölümünü görüntüleyebilirsiniz. Gönderen bilgilerinin bir parçası iletide aracılar için görünür hale getirmek gereken ancak müdahale değil, yalnızca olabilir emin olmak istiyor imzaladıktan ancak şifrelenmemiş bırakın. İmza iletisinin bir parçası olduğundan, ultimate alıcı iletiyi bilgilerinde bozulmadan alındı doğrulayabilirsiniz. Bir senaryo eylem üstbilgi değeri göre yollar ileti hizmeti bir SOAP aracı olabilir. Varsayılan olarak, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] eylemi değeri şifrelemez ancak ileti güvenliği kullandıysanız imzalar. Bu nedenle, bu bilgiler tüm aracılar için kullanılabilir, ancak hiç kimsenin değiştirebilirsiniz.  
  
-   Birden çok aktarımı için destek. Güvenlik protokolü Bel gerek kalmadan Adlandırılmış Kanallar ve TCP, gibi birçok farklı taşımaları üzerinden güvenli iletiler gönderebilir. Aktarım düzeyi güvenlik, tüm güvenlik bilgilerini tek özel taşımanın bağlantı kapsamlıdır ve ileti içeriği kendisini kullanılabilir değil. İleti güvenliği iletinin ileti ve güvenlik bağlamı iletmek için kullandığınız hangi aktarım doğrudan ileti içine katıştırılmış bağımsız olarak güvenli hale getirir.  
  
-   Geniş bir dizi kimlik bilgilerini ve talepler için destek. İleti güvenliği talep SOAP iletisi içinde herhangi bir türde gönderebilen genişletilebilir bir çerçeve sağlar WS-Security belirtimi temel alır. Taşıma güvenliği farklı olarak, kimlik doğrulama mekanizması veya kullanabileceğiniz talep kümesi taşıma özellikleri tarafından sınırlı değildir. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ileti güvenliği ve gerektiği gibi ek türlerini desteklemek için Genişletilebilir kimlik doğrulama ve talep iletim birden çok türde içerir. Bu nedenlerle, örneğin, bir Federasyon kimlik senaryosu ileti güvenliği mümkün değildir. Federasyon senaryolarında WCF desteklediği hakkında daha fazla bilgi için bkz: [Federasyon ve verilen belirteçleri](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="how-message-and-transport-security-compare"></a>İleti ve taşıma güvenliği nasıl Karşılaştır  
  
### <a name="pros-and-cons-of-transport-level-security"></a>Artıları ve eksileri aktarım düzeyinde güvenlik  
 Taşıma güvenliği aşağıdaki avantajlara sahiptir:  
  
-   İletişim kuran taraflar XML düzeyi güvenlik kavramları anlamanız gerektirmez. Örneğin, HTTPS iletişimi korumak için kullanıldığında, bu birlikte çalışabilirlik iyileştirebilir.  
  
-   Genellikle Gelişmiş performans.  
  
-   Donanım Hızlandırıcıları kullanılabilir.  
  
-   Akış mümkündür.  
  
 Taşıma güvenliği aşağıdaki dezavantajları bulunur:  
  
-   Atlama için-atlama yalnızca.  
  
-   Sınırlı ve inextensible kimlik bilgileri kümesi.  
  
-   Aktarım bağımlı.  
  
### <a name="disadvantages-of-message-level-security"></a>İleti düzeyi güvenlik dezavantajları  
 İleti güvenliği aşağıdaki dezavantajları bulunur:  
  
-   Performans  
  
-   İleti akış kullanamazsınız.  
  
-   XML düzeyi güvenlik mekanizmaları ve Destek, WS-Security belirtimi için gerektirir. Bu, birlikte çalışabilirlik etkileyebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Aktarım Güvenliği](../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [Nasıl yapılır: Aktarım Güvenliği ve İleti Kimlik Bilgilerini Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)  
 [Microsoft desenleri ve uygulamalar, Bölüm 3: uygulama taşıma ve ileti güvenlik katmanı](http://go.microsoft.com/fwlink/?LinkId=88897)
