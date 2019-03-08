---
title: WCF'de İleti Güvenliği
ms.date: 03/30/2017
ms.assetid: a80efb59-591a-4a37-bb3c-8fffa6ca0b7d
ms.openlocfilehash: 9c63e035d295860ea29dbbcd66bfd4527d837de4
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57674022"
---
# <a name="message-security-in-wcf"></a>WCF'de İleti Güvenliği

Windows Communication Foundation (WCF) güvenlik sağlamak için iki ana modu vardır (`Transport` ve `Message`) ve üçüncü modu (`TransportWithMessageCredential`), iki birleştirir. Bu konu, ileti güvenliği ve nedenleri kullanılacağını açıklar.

## <a name="what-is-message-security"></a>İleti güvenliği nedir?

İleti güvenliği WS-Security belirtimi iletileri güvenli hale getirmek için kullanır. WS-Security belirtimi, gizlilik, bütünlük ve kimlik doğrulaması (aktarım düzeyi) yerine SOAP ileti düzeyinde emin olmak için Mesajlaşma SOAP yapılan geliştirmeleri açıklar.

Kısaca, ileti güvenliği, güvenlik kimlik bilgileri ve herhangi bir ileti koruma (imzalama veya şifreleme) yanı sıra her bir ileti ile talep kapsülleyerek aktarım güvenliği ' farklıdır. Güvenlik içeriği değiştirerek iletiyi doğrudan uygulama güvenli bir ileti ile ilgili güvenlik konuları içeren kendi kendine olmasını sağlar. Bu aktarım güvenliği kullanıldığında, mümkün olmayan bazı senaryolar sağlar.

## <a name="reasons-to-use-message-security"></a>İleti güvenliği kullanma nedenleri

İleti düzeyi güvenlik, tüm güvenlik bilgileri saklanmış olduğu iletisi. İleti düzeyi güvenliği yerine aktarım düzeyi güvenlik ile ileti güvenliği aşağıdaki avantajlara sahiptir:

- Uçtan uca güvenlik. Noktadan noktaya iletişim olduğunda aktarım güvenliği, Güvenli Yuva Katmanı (SSL) gibi iletileri yalnızca güvenliğini sağlar. İleti ultimate alıcı ulaşmadan önce bir veya daha fazla SOAP aracıları (örneğin bir yönlendirici) için yönlendirilir, isteğe bağlı olarak bir aracı hattan okur sonra ileti korumalı değil. Ayrıca, istemci kimlik doğrulama bilgilerini yalnızca ilk aracı için kullanılabilir ve bant dışı bir şekilde ultimate alıcısına gerekirse yeniden iletilmesi gerekir. SSL güvenlik tek atlama arasında tüm yol kullansa bile bu geçerlidir. İleti güvenliği doğrudan ileti ile çalışır ve XML'de güvenliğini sağlar çünkü güvenlik iletisi ultimate alıcı ulaşmadan önce kaç aracılar dahil bağımsız olarak kalır. Bu, doğru uçtan uca güvenlik senaryosu sağlar.

- Daha fazla esneklik. İletinin tamamı yerine ileti bölümlerini imzalanmış veya şifrelenmiş. Başka bir deyişle, aracılar için tasarlanmıştır ileti bölümlerini görüntüleyebilirsiniz. Gönderen bilgi parçası iletisinde aracılar için görünür duruma getirmek için gerekli, ancak bunu ile müdahaleye uğramadığından emin olmak istiyor, bunu yalnızca imzalayın ancak şifrelenmemiş bırakın. İmza iletisinin bir parçası olduğundan, ultimate alıcı bilgi iletisi bozulmadan alındığını doğrulayabilirsiniz. Bir senaryo, bir SOAP aracı eylemi üst bilgi değeri göre yollar ileti hizmet olabilir. Varsayılan olarak, WCF, eylem değerini şifrelemez ancak ileti güvenliği kullanılıyorsa, oturum açtığında. Bu nedenle, bu bilgiler, tüm aracılar için kullanılabilir, ancak hiç değiştirebilirsiniz.

- Birden çok aktarımı için destek. İçin güvenlik protokolü kullanan gerek kalmadan Adlandırılmış Kanallar ve, TCP gibi çok sayıda farklı taşımalar üzerinden güvenli iletiler gönderebilirsiniz. Aktarım düzeyi güvenlik ile tüm güvenlik bilgilerini tek bir belirli taşıma bağlantısı kapsamlıdır ve ileti içeriği kendisini kullanılabilir değil. İleti güvenliği iletinin ileti ve güvenlik bağlamı iletmek için kullandığınız aktarım doğrudan ileti içine katıştırılmış bağımsız olarak güvenli hale getirir.

- Çok sayıda kimlik bilgilerini ve talepler için destek. İleti güvenliği talep SOAP iletisi içinde herhangi bir türde aktarabilen genişletilebilir bir çerçeve sağlar WS-güvenlik belirtimi temel alır. Aktarım güvenliği, kimlik doğrulama mekanizmaları veya kullanabileceğiniz talep kümesini taşıma özellikleri ile sınırlı değildir. WCF ileti güvenliğini birden çok kimlik doğrulaması ve talep iletim içerir ve gerektiğinde ek türlerini destekleyecek şekilde genişletilebilir. Bu nedenlerle, örneğin, bir Federasyon kimlik senaryosu ileti güvenliği mümkün değildir. Federasyon senaryolarında WCF desteklediği hakkında daha fazla bilgi için bkz. [Federasyon ve verilen belirteçler](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).

## <a name="how-message-and-transport-security-compare"></a>İleti ve aktarım güvenliği nasıl karşılaştırın

### <a name="pros-and-cons-of-transport-level-security"></a>Artıları ve eksileri aktarım düzeyi güvenlik

Aktarım güvenliği aşağıdaki avantajlara sahiptir:

- İletişim kuran taraflar XML düzeyinde güvenlik kavramları anlama gerektirmez. Örneğin, HTTPS iletişimi güvenli hale getirmek için kullanıldığında, bu birlikte çalışabilirlik artırabilir.

- Genel olarak performansı İyileştirildi.

- Donanım Hızlandırıcıları kullanılabilir.

- Akış mümkündür.

 Aktarım güvenliği aşağıdaki dezavantajları bulunur:

- Atlama için-atlama yalnızca.

- Kimlik bilgileri sınırlandırırız ve inextensible kümesi.

- Aktarım bağlıdır.

### <a name="disadvantages-of-message-level-security"></a>İleti düzeyi güvenliği dezavantajları

İleti güvenliği aşağıdaki dezavantajları bulunur:

- Performans

- İleti akışı kullanamazsınız.

- Uygulama, XML düzeyinde güvenlik mekanizmalar ve destek için WS-Security belirtimi gerektirir. Bu, birlikte çalışabilirlik etkileyebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Aktarım Güvenliği](../../../../docs/framework/wcf/feature-details/transport-security.md)
- [Nasıl yapılır: Kullanım taşıma Güveniği ve ileti kimlik bilgileri](../../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)
- [Microsoft desenler ve uygulamalar, Bölüm 3: Uygulama aktarım ve ileti Katmanı Güvenliği](https://go.microsoft.com/fwlink/?LinkId=88897)
