---
title: Sözleşmeler
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], contracts
- contracts [WCF]
- Windows Communication Foundation [WCF], contracts
ms.assetid: c8364183-4ac1-480b-804a-c5e6c59a5d7d
ms.openlocfilehash: 0443e5b37e637351d6491c37ec443c93636460a3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134894"
---
# <a name="contracts"></a>Sözleşmeler
Bu bölümde Windows Communication Foundation (WCF) sözleşmeleri tanımlaması ve gösterilmektedir. Ne bir uç nokta için dış dünya iletişim kuran bir hizmet sözleşmesi belirler. Daha somut bir düzeyde istek/yanıt gibi tek yönlü ve çift yönlü bir dizi temel ileti exchange desenleri (MEPs) ile düzenlenmiş belirli ileti hakkında bir deyim olduğu. Bir hizmet sözleşmesini ileti alışverişlerinde mantıksal olarak ilişkili bir dizi ise, bir hizmet işlemi bir tek ileti alışverişi olur. Örneğin, bir `Hello` işlemi (arayan Karşılama duyurmaktan biçimde) bir ileti açıkça kabul etmelidir ve olabilir veya (işlemin ilgili bağlı olarak) bir ileti döndürmeyebilir.  
  
 Sözleşmeler ve diğer temel WCF kavramları hakkında daha fazla bilgi için bkz. [temel Windows Communication Foundation kavramları](../../../../docs/framework/wcf/fundamental-concepts.md). Bu konu başlığı altında hizmet sözleşmelerini anlamaya odaklanır. Hizmet sözleşmeleri hizmetlerine bağlanmak için kullanan istemciler oluşturma hakkında daha fazla bilgi için bkz. [WCF istemcisi genel bakış](../../../../docs/framework/wcf/wcf-client-overview.md). İstemci kanalları, istemci mimarisi ve diğer istemci sorunları hakkında daha fazla bilgi için bkz: [istemciler](../../../../docs/framework/wcf/feature-details/clients.md).  
  
## <a name="overview"></a>Genel Bakış  
 Bu konu, WCF hizmetleri tasarlama ve uygulama için bir üst düzey kavramsal yönlendirme sağlar. Konuları daha ayrıntılı tasarlama ve uygulama özellikleri hakkında bilgi sağlar. Tasarlama ve uygulama WCF uygulamanızı önce önerilen aldığınız:  
  
-   Anlamak hizmet sözleşmesini ne olduğu, nasıl çalıştığını ve nasıl oluşturacağınızı.  
  
-   Sözleşmeler en düşük gereksinimleri durumunu anlamak, çalışma zamanı yapılandırma veya barındırma ortamı değil destekleyebilir.  
  
## <a name="service-contracts"></a>Hizmet Sözleşmeleri  
 Bir hizmet sözleşmesini hakkında bilgi sağlayan bir açıklamadır:  
  
-   Bir hizmet işlemlerinde gruplandırmasıdır.  
  
-   İşlem iletileri değiş tokuş imzası.  
  
-   Bu iletileri veri türleri.  
  
-   İşlemleri konumu.  
  
-   Başarılı iletişim hizmetiyle desteklemek için kullanılan serileştirme biçimleri ve belirli protokoller.  
  
 Örneğin, bir satın alma siparişi sözleşme olabilir bir `CreateOrder` sipariş bilgileri bir girişi kabul eden bir işlem türleri ve siparişi tanımlayıcısı dahil olmak üzere, başarı veya başarısızlık durumu bilgilerini döndürür. Ayrıca olabilir bir `GetOrderStatus` işlemi, bir siparişi tanımlayıcısı kabul eden ve sipariş durumu bilgilerini döndürür. Bu tür bir hizmet sözleşmesini belirtmeniz gerekir:  
  
-   Satın alma siparişi sözleşme, toplamda `CreateOrder` ve `GetOrderStatus` operations.  
  
-   İşlemleri belirttiğiniz iletileri giriş ve çıkış iletileri.  
  
-   Bu iletiler gerçekleştirebilirsiniz veriler.  
  
-   Kategorik deyimleri hakkında iletişim altyapısı başarıyla iletileri işlemek için gerekli. Örneğin, bu Ayrıntılar arasında olup olmadığını ve hangi güvenlik formları başarılı iletişim kurmak için gereklidir.  
  
 Bu tür bir uygulama bilgileri (Microsoft olmayan platformlar dahil) diğer platformlarda iletmek için XML hizmet sözleşmelerini herkese açık şekilde standart XML biçimlerde, gibi ifade edilir [Web Hizmetleri Açıklama Dili (WSDL)](https://go.microsoft.com/fwlink/?LinkId=87004) ve [XML Şeması (XSD)](https://go.microsoft.com/fwlink/?LinkId=87005), diğerlerinin yanı sıra. Geliştiriciler için birçok platformda dil belirtiminin anladıkları olduğundan hem dillere birlikte çalışabilirliği etkinleştirmek için tasarlandığından hizmet ile iletişim kurabilen uygulamaları oluşturmak için bu genel sözleşme bilgileriniz kullanabilirsiniz Genel form, biçimleri ve protokolleri hizmetinin desteklediği açıklayarak. WCF bu tür bilgileri nasıl işlediği hakkında daha fazla bilgi için bkz. [meta verileri](../../../../docs/framework/wcf/feature-details/metadata.md).  
  
 Sözleşmeler ifade edilemez pek çok yolla, ancak ve WSDL ve XSD Hizmetleri erişilebilir bir şekilde tanımlamak için mükemmel dilleri olsa da, bunlar doğrudan kullanmak zor dilleri — yalnızca bir hizmet, olmayan hizmet sözleşmesi açıklamaları oldukları herhangi bir durumda, uygulamaları. Bu nedenle, WCF uygulamaları yapısını tanımlayan ve hizmet uygulamak için yönetilen öznitelikleri, arabirimler ve sınıflar kullanın.  
  
 Yönetilen türlerinde tanımlanan elde edilen sözleşme dönüştürülebilir (olarak da bilinir *dışarı*) olarak meta verileri — WSDL ve XSD — istemciler veya diğer hizmet uygulayıcılar, özellikle diğer platformlarda gerektiğinde. Sonuç tüm istemci uygulamaları için ortak meta verileri kullanarak açıklanan basit bir programlama modelidir. Nakliye ve güvenlikle ilgili bilgiler gibi temel SOAP iletilerini ayrıntılarını, gerekli ve türlerinden dönüşümler hizmet sözleşme tür sistemi XML türü sistemine otomatik olarak gerçekleştiren WCF bırakılabilir.  
  
 Sözleşmeleri tasarlama hakkında daha fazla bilgi için bkz. [Hizmet sözleşmeleri tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md). Sözleşmelerini uygulama hakkında daha fazla bilgi için bkz. [hizmet sözleşmelerini uygulama](../../../../docs/framework/wcf/implementing-service-contracts.md).  
  
 Ayrıca, WCF hizmet sözleşmeleri ileti düzeyinde tamamen geliştirme olanağı da sağlar. Hizmet sözleşmeleri ileti düzeyinde geliştirme hakkında daha fazla bilgi için bkz. [kullanarak ileti sözleşmeleri](../../../../docs/framework/wcf/feature-details/using-message-contracts.md). Hizmetleri, SOAP XML olmayan geliştirme hakkında daha fazla bilgi için bkz. [POX uygulamaları ile birlikte çalışabilirlik](../../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md).  
  
### <a name="understanding-the-hierarchy-of-requirements"></a>Hiyerarşi gereksinimlerini anlama  
 Bir hizmet sözleşmesini işlemleri grupları; İleti türleri MEP belirtir ve bu iletileri carry veri türlerini; çalışma zamanı davranışını uygulama destek sözleşmesi olmalıdır kategorilerini belirtir (örneğin, iletileri imzalı şifrelenir ve gerekli olabilir). Ancak, hizmet anlaşması kendisi, tam olarak nasıl Bu gereksinimler, yalnızca, olması gereken karşılandığından belirtmiyor. Hangi şifreleme veya nasıl bir ileti imzalanır en fazla uygulama ve uyumlu bir hizmet yapılandırmasını türüdür.  
  
 Sözleşme davranış eklemek için belirli şeyleri hizmet sözleşmesi uygulama ve çalışma zamanı yapılandırma gerektiren şekilde dikkat edin. Önceki gereksinimler kümesine kullanmak için bir hizmeti kullanıma sunmak için karşılanması gereken gereksinimleri kümesini oluşturur. Bir sözleşme uygulama gereksinimlerini yaparsa, bir uygulama henüz gerektirebilir daha fazla çalıştırmak hizmet bağlamaları ve yapılandırma. Son olarak, ana bilgisayar uygulaması hizmet yapılandırması ve bağlamalar eklemek gereksinimlere desteklemelidir.  
  
 Bu ek gereksinim işlem tasarlama, uygulama, yapılandırma ve Windows Communication Foundation (WCF) hizmet uygulamanızı barındıran çalışırken göz önünde bulundurmanız önemlidir. Örneğin, sözleşmenin bir oturumu desteklemek gerektiğini belirtebilirsiniz. Bu durumda, sözleşmeye dayalı bu gereksinimi desteklemek için bağlama yapılandırmanız gerekir ya da hizmet uygulamasında çalışmaz. Ya da hizmetiniz, tümleşik Windows kimlik doğrulaması gerektiriyor ve Internet Information Services (IIS) barındırılan hizmetin içinde bulunduğu Web uygulamasının tümleşik Windows kimlik doğrulaması açık ve kapalı anonim destek sahip olmanız gerekir. Farklı hizmet konak uygulama türleri etkisini ve özellikleri hakkında daha fazla bilgi için bkz. [barındırma](../../../../docs/framework/wcf/feature-details/hosting.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uç Noktalar: Adresler, Bağlamalar ve Sözleşmeler](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [Hizmet Sözleşmeleri Tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md)
- [Hizmet Sözleşmelerini Uygulama](../../../../docs/framework/wcf/implementing-service-contracts.md)
