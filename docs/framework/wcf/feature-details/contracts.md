---
title: Sözleşmeler
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], contracts
- contracts [WCF]
- Windows Communication Foundation [WCF], contracts
ms.assetid: c8364183-4ac1-480b-804a-c5e6c59a5d7d
ms.openlocfilehash: 8522ae89ca69ec594f62e272f8479b607609f064
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493273"
---
# <a name="contracts"></a>Sözleşmeler
Bu bölümde tanımlayın ve Windows Communication Foundation (WCF) sözleşmeleri uygulamak gösterilmektedir. Bir hizmet sözleşmesini ne bir uç nokta için dış dünya iletişim kurar belirtir. Daha somut bir düzeyde, bu temel ileti exchange desenleri (MEPs) düzenlenmiştir belirli iletileri kümesi hakkında istek/yanıt gibi tek yönlü ve çift yönlü açıklamadır. Bir hizmet sözleşmesini ileti alışverişlerinde mantıksal olarak ilişkili bir dizi, bir hizmet işlemi tek bir ileti exchange ise. Örneğin, bir `Hello` işlemi (arayan Tebrik Duyurusu şekilde) açıkça bir ileti kabul etmeniz gerekir ve olabilir veya (işlemi geçici kullanım bağlı olarak) bir ileti döndürmeyebilir.  
  
 Sözleşmeler ve diğer temel WCF kavramlar hakkında daha fazla bilgi için bkz: [temel Windows Communication Foundation kavramları](../../../../docs/framework/wcf/fundamental-concepts.md). Bu konu, hizmet sözleşmelerini anlamaya odaklanır. Hizmet sözleşmeleri hizmetlerine bağlanmak için kullanan istemciler oluşturma hakkında daha fazla bilgi için bkz: [WCF istemcisi genel bakış](../../../../docs/framework/wcf/wcf-client-overview.md). İstemci kanalları, istemci mimarisi ve diğer istemci sorunları hakkında daha fazla bilgi için bkz: [istemcileri](../../../../docs/framework/wcf/feature-details/clients.md).  
  
## <a name="overview"></a>Genel Bakış  
 Bu konu, WCF hizmetleri tasarlama ve uygulama için bir üst düzey kavramsal yönlendirmesini sağlar. Konuları daha ayrıntılı tasarlama ve uygulama özellikleri hakkında bilgi sağlar. Tasarlama ve WCF uygulamanızın uygulama önce önerilen doğrulayın:  
  
-   Anlamak hizmet sözleşmesini ne olduğu, nasıl çalıştığı ve nasıl oluşturulacağı.  
  
-   Sözleşmeleri en düşük gereksinimler durumunu anlamak, çalışma zamanı yapılandırma veya barındırma ortamı desteklemiyor.  
  
## <a name="service-contracts"></a>Hizmet Sözleşmeleri  
 Bir hizmet sözleşmesini hakkında bilgi sağlayan bir açıklamadır:  
  
-   Bir hizmet işlemlerinde gruplandırması.  
  
-   Değiştirilen iletilerin açısından işlemleri imzası.  
  
-   Bu iletileri veri türleri.  
  
-   Operations konumu.  
  
-   Belirli protokolleri ve hizmeti ile başarılı iletişimi desteklemek için kullanılan serileştirme biçimleri.  
  
 Örneğin, bir satın alma siparişi sözleşme olabilir bir `CreateOrder` bir giriş sırası bilgilerinin kabul işlemi türleri ve bir sıra tanımlayıcısını dahil olmak üzere, başarı veya başarısızlık bilgileri döndürür. Ayrıca olabilir bir `GetOrderStatus` sipariş tanımlayıcı kabul edip sipariş durum bilgilerini döndürür işlemi. Bu tür bir hizmet sözleşmesini belirtmeniz gerekir:  
  
-   Satın alma siparişi sözleşme, oluşmuştur `CreateOrder` ve `GetOrderStatus` işlemleri.  
  
-   Operations belirttiğiniz iletileri giriş ve ileti çıkışı.  
  
-   Bu iletiler taşıyabilir veriler.  
  
-   Kategorik deyimleri başarıyla iletileri işlemek için gerekli iletişimini altyapısıyla ilgili. Örneğin, bu ayrıntıları dahil olup olmadığını ve hangi forms güvenlik başarıyla iletişim kurabilmek için sahip gereklidir.  
  
 Bu tür uygulamalar için bilgileri diğer platformlarda (dahil olmak üzere Microsoft dışı platformlar) iletmek için XML Hizmet sözleşmeleri genel olarak standart XML biçimlerde gibi belirtilmiştir [Web Hizmetleri Açıklama Dili (WSDL)](http://go.microsoft.com/fwlink/?LinkId=87004) ve [XML Şeması (XSD)](http://go.microsoft.com/fwlink/?LinkId=87005), diğerlerinin yanı sıra. Geliştiriciler için birçok platformda belirtimi dili anlamaları için hem dillere birlikte çalışabilirliği sağlamak için tasarlandığından hizmeti ile iletişim kurabilen uygulamaları oluşturmak için bu ortak sözleşme bilgilerini kullanabilirsiniz Genel form, biçimleri ve protokolleri hizmetini destekleyen açıklayarak. WCF bu tür bilgileri nasıl işlediği hakkında daha fazla bilgi için bkz: [meta verileri](../../../../docs/framework/wcf/feature-details/metadata.md).  
  
 Sözleşmeleri ifade edilir birçok yolu, ancak ve WSDL ve XSD Hizmetleri erişilebilir bir biçimde tanımlamak için mükemmel dilleri olsa da, bunlar doğrudan kullanılacak zor dilleri — yalnızca bir hizmet, değil hizmet sözleşmesi açıklamalarını oldukları herhangi bir durumda uygulamaları. Bu nedenle, WCF uygulamaları yapısını tanımlar ve bir hizmet uygulamak için yönetilen öznitelikleri, arabirimleri ve sınıfları kullanın.  
  
 Yönetilen türlerinde tanımlanan ortaya çıkan sözleşmeyi dönüştürülebilir (olarak da bilinir *dışarı*) meta veri olarak — WSDL ve XSD — istemciler veya diğer platformlarda özellikle diğer hizmet Implementers gerektiğinde. Sonuç herhangi bir istemci uygulama için ortak meta verileri kullanarak açıklanan basit bir programlama modelidir. Gerekli ve türlerinden dönüşümler hizmet sözleşmesi tür sistemi XML türü sistemine otomatik olarak gerçekleştirir WCF için güvenlikle ilgili bilgiler ve taşıma gibi temel alınan SOAP iletilerine ayrıntılarını bırakılabilir.  
  
 Sözleşmeleri tasarlama hakkında daha fazla bilgi için bkz: [Hizmet sözleşmeleri tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md). Sözleşmelerini uygulama hakkında daha fazla bilgi için bkz: [hizmet sözleşmelerini uygulama](../../../../docs/framework/wcf/implementing-service-contracts.md).  
  
 Ayrıca, WCF hizmet sözleşmeleri ileti düzeyinde tamamen geliştirme olanağı sağlar. Hizmet sözleşmeleri ileti düzeyinde geliştirme hakkında daha fazla bilgi için bkz: [kullanarak ileti sözleşmeleri](../../../../docs/framework/wcf/feature-details/using-message-contracts.md). Hizmetleri SOAP olmayan XML içinde geliştirme hakkında daha fazla bilgi için bkz: [POX uygulamaları ile birlikte çalışabilirlik](../../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md).  
  
### <a name="understanding-the-hierarchy-of-requirements"></a>Gereksinimleri hiyerarşisini anlama  
 Bir hizmet sözleşmesini operations grupları; İleti türleri MEP belirtir ve bu iletileri taşıyan veri türleri; çalışma zamanı davranışını sözleşme desteklemek için bir uygulama olmalıdır kategorilerini belirtir (örneğin, iletileri imzalanmış ve şifrelenecek olduğunu gerektiren). Ancak, hizmet sözleşmesini kendisi, tam olarak nasıl bu gereksinimleri, yalnızca, olması gereken karşılandığından belirtmiyor. Hangi şifreleme veya nasıl bir ileti imzalı uygulama ve uyumlu bir hizmet yapılandırmasını kadar türüdür.  
  
 Sözleşme davranışı eklemek için belirli konular hizmet sözleşmesini uygulama ve çalışma zamanı yapılandırma gerektirir şekilde dikkat edin. Bir hizmeti kullanmak için kullanıma sunmak için karşılanması gereken gereksinimleri kümesi gereksinimleri önceki kümesinde oluşturur. Bir sözleşme uygulama gereksinimlerini yaparsa, bir uygulama henüz gerektirebilir için yapılandırma ve çalıştırmak hizmeti etkinleştirmek bağlamaları daha fazla. Son olarak, konak uygulama hizmet yapılandırması bağlamaları Ekle ve herhangi bir gereksinimi desteklemelidir.  
  
 Bu ek gereksinim işlem tasarlama, uygulama, yapılandırma ve Windows Communication Foundation (WCF) hizmetini uygulamanızı barındıran çalışırken göz önünde bulundurmanız önemlidir. Örneğin, sözleşmenin bir oturum desteklemek gerektiğini belirtebilirsiniz. Bu durumda, bağlama sözleşme bu gereksinimi desteklemek için yapılandırmanız gerekir ya da hizmet uygulaması çalışmaz. Veya hizmetinizi tümleşik Windows kimlik doğrulaması gerektiriyorsa ve Internet Information Services (IIS) barındırılan hizmetin bulunduğu Web uygulaması Tümleşik Windows kimlik doğrulaması açık ve kapalı anonim destek olması gerekir. Farklı hizmet ana uygulama türleri etkisini ve özellikler hakkında daha fazla bilgi için bkz: [barındırma](../../../../docs/framework/wcf/feature-details/hosting.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uç Noktalar: Adresler, Bağlamalar ve Anlaşmalar](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [Hizmet Sözleşmeleri Tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md)  
 [Hizmet Anlaşmalarını Uygulama](../../../../docs/framework/wcf/implementing-service-contracts.md)
