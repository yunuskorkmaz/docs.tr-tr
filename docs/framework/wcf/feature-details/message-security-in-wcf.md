---
title: WCF'de İleti Güvenliği
ms.date: 03/30/2017
ms.assetid: a80efb59-591a-4a37-bb3c-8fffa6ca0b7d
ms.openlocfilehash: 32f6659f6ac744ab7af07c23e7e26ea1124d020c
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212065"
---
# <a name="message-security-in-wcf"></a>WCF'de İleti Güvenliği

Windows Communication Foundation (WCF), güvenlik sağlamak için iki ana moda sahiptir (`Transport` ve `Message`) ve ikisini birleştiren üçüncü bir mod (`TransportWithMessageCredential`). Bu konuda ileti güvenliği ve kullanma nedenleri ele alınmaktadır.

## <a name="what-is-message-security"></a>Ileti güvenliği nedir?

İleti güvenliği, iletileri güvenli hale getirmek için WS-Security belirtimini kullanır. WS-Security belirtimi SOAP ileti düzeyinde gizlilik, bütünlük ve kimlik doğrulaması sağlamak için SOAP mesajlaşma iyileştirmeleri tanımlar (aktarım düzeyi yerine).

Kısaca ileti güvenliği, her iletiyle birlikte güvenlik kimlik bilgilerini ve taleplerini kapsülleyerek (imzalama veya şifreleme), aktarım güveninden farklıdır. İçeriğini değiştirerek güvenlik doğrudan iletiye uygulandığında, güvenli iletinin güvenlik yönlerine göre kendi kendine birlikte içerme olanağı sağlanır. Bu, aktarım güvenliği kullanıldığında mümkün olmayan bazı senaryolar sunar.

## <a name="reasons-to-use-message-security"></a>Ileti güvenliğini kullanma nedenleri

İleti düzeyinde güvenlik bölümünde, tüm güvenlik bilgileri iletide kapsüllenir. Aktarım düzeyi güvenlik yerine ileti düzeyinde güvenlikle iletinin güvenliğini sağlamak aşağıdaki avantajları içerir:

- Uçtan uca güvenlik. Güvenli Yuva Katmanı (SSL) gibi aktarım güvenliği, yalnızca iletişim noktadan noktaya olduğunda iletileri korur. İleti, son alıcıya ulaşmadan önce bir veya daha fazla SOAP aracısıyla (örneğin, bir yönlendirici) yönlendirilirse, bir aracı onu kablodan okuduktan sonra ileti korunmaz. Ayrıca, istemci kimlik doğrulama bilgileri yalnızca ilk aracı tarafından kullanılabilir ve gerekirse bant dışı olarak son alıcıya yeniden aktarılmalıdır. Bu, tüm yolun bireysel atlama arasında SSL güvenliği kullanması durumunda bile geçerlidir. İleti güvenliği iletiyle doğrudan çalıştığı ve içindeki XML 'nin güvenliğini sağladığından, son alıcıya ulaşmadan önce kaç aracı dahil ettiğinize bakılmaksızın güvenlik iletiyle birlikte kalır. Bu, doğru uçtan uca bir güvenlik senaryosu sağlar.

- Daha fazla esneklik. İletinin tamamı yerine ileti parçaları imzalanabilir veya şifrelenebilir. Bu, aracıların kendisine yönelik ileti parçalarını görüntüleyebileceği anlamına gelir. Gönderenin, iletideki bilgilerin bir kısmını aracıların görebilmesi, ancak üzerinde oynanmamasını sağlamak isterse, bu, yalnızca imzalayıp şifrelenmemiş olarak bırakabilirsiniz. İmza iletinin bir parçası olduğundan, son alıcı iletideki bilgilerin bozulmadan alındığını doğrulayabilirler. Bir senaryoda iletiyi eylem üst bilgi değerine göre yönlendiren bir SOAP aracı hizmeti olabilir. Varsayılan olarak, WCF eylem değerini şifrelemez, ancak ileti güvenliği kullanılıyorsa bunu imzalar. Bu nedenle, bu bilgiler tüm aracılar tarafından kullanılabilir, ancak kimse bunu değiştiremezler.

- Birden çok aktarım için destek. Güvenlik protokolüne güvenmeleri gerekmeden, adlandırılmış kanallar ve TCP gibi birçok farklı aktarımdan güvenli iletiler gönderebilirsiniz. Aktarım düzeyi güvenliği sayesinde, tüm güvenlik bilgileri tek bir belirli aktarım bağlantısı kapsamına alınır ve ileti içeriğinin kendisi tarafından kullanılamaz. İleti güvenliği iletiyi aktarmak için kullandığınız aktarımdan bağımsız olarak iletiyi güvenli hale getirir ve güvenlik bağlamı doğrudan iletinin içine katıştırılır.

- Geniş bir kimlik bilgileri ve talepler kümesi için destek. İleti güvenliği, SOAP iletisinde herhangi bir tür talep gönderebilen genişletilebilir bir çerçeve sağlayan WS-Security belirtimini temel alır. Aktarım güvenliğinin aksine, kullanabileceğiniz kimlik doğrulama mekanizmaları veya talepler kümesi, taşıma özellikleri ile sınırlı değildir. WCF ileti güvenliği, birden çok kimlik doğrulaması ve talep iletimi içerir ve gerektiğinde ek türleri desteklemek için genişletilebilir. Örneğin, bu nedenlerle bir federal kimlik bilgileri senaryosu ileti güvenliği olmadan mümkün değildir. WCF tarafından desteklenen Federasyon senaryoları hakkında daha fazla bilgi için bkz. [Federasyon ve verilen belirteçler](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).

## <a name="how-message-and-transport-security-compare"></a>Ileti ve taşıma güvenliği nasıl karşılaştırılır

### <a name="pros-and-cons-of-transport-level-security"></a>Aktarım düzeyi güvenliği için olumlu ve olumsuz yönleri

Taşıma güvenliği aşağıdaki avantajları içerir:

- , İletişim kuran tarafların XML düzeyi güvenlik kavramlarını anlamasına gerek yoktur. Bu, örneğin HTTPS 'yi güvenli hale getirmek için HTTPS kullanıldığında, birlikte çalışabilirliğini iyileştirebilir.

- Genel olarak gelişmiş performans.

- Donanım hızlandırıcıları kullanılabilir.

- Akış mümkündür.

 Taşıma güvenliği aşağıdaki dezavantajlara sahiptir:

- Yalnızca atlama atlama.

- Sınırlı ve Genişletilebilir kimlik bilgileri kümesi.

- Aktarıma bağımlı.

### <a name="disadvantages-of-message-level-security"></a>Ileti düzeyinde güvenliğin dezavantajları

İleti güvenliği aşağıdaki dezavantajlara sahiptir:

- Performans

- İleti akışı kullanılamıyor.

- XML düzeyi güvenlik mekanizmalarının uygulanmasını ve WS-Security belirtimi desteğini gerektirir. Bu işlem, birlikte çalışabilirliği etkileyebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Aktarım Güvenliği](../../../../docs/framework/wcf/feature-details/transport-security.md)
- [Nasıl yapılır: Aktarım Güvenliği ve İleti Kimlik Bilgilerini Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)
- [Microsoft desenleri ve uygulamaları, Bölüm 3: taşıma ve Ileti Katmanı Güvenliği uygulama](https://docs.microsoft.com/previous-versions/msp-n-p/ff647370(v=pandp.10))
