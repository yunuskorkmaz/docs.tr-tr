---
title: "Sözleşmeler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF [WCF], contracts
- contracts [WCF]
- Windows Communication Foundation [WCF], contracts
ms.assetid: c8364183-4ac1-480b-804a-c5e6c59a5d7d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9a45fc606ac962b4dc7aac8b49ed9a3c6c421ccd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="contracts"></a>Sözleşmeler
Bu bölümde tanımlamak ve uygulamak gösterilmiştir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]sözleşmeleri. Bir hizmet sözleşmesini ne bir uç nokta için dış dünya iletişim kurar belirtir. Daha somut bir düzeyde, bu temel ileti exchange desenleri (MEPs) düzenlenmiştir belirli iletileri kümesi hakkında istek/yanıt gibi tek yönlü ve çift yönlü açıklamadır. Bir hizmet sözleşmesini ileti alışverişlerinde mantıksal olarak ilişkili bir dizi, bir hizmet işlemi tek bir ileti exchange ise. Örneğin, bir `Hello` işlemi (arayan Tebrik Duyurusu şekilde) açıkça bir ileti kabul etmeniz gerekir ve olabilir veya (işlemi geçici kullanım bağlı olarak) bir ileti döndürmeyebilir.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]sözleşmeler ve diğer temel [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bkz, [temel Windows Communication Foundation kavramları](../../../../docs/framework/wcf/fundamental-concepts.md). Bu konu, hizmet sözleşmelerini anlamaya odaklanır. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]hizmeti kullanan istemciler oluşturma sözleşmeleri hizmetlerine bağlanmak için bkz: [WCF istemcisi genel bakış](../../../../docs/framework/wcf/wcf-client-overview.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]bkz: istemci kanalları, istemci mimarisi ve diğer istemci sorunları [istemcileri](../../../../docs/framework/wcf/feature-details/clients.md).  
  
## <a name="overview"></a>Genel Bakış  
 Bu konu, tasarlama ve uygulama için bir üst düzey kavramsal yönlendirmesini sağlar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri. Konuları daha ayrıntılı tasarlama ve uygulama özellikleri hakkında bilgi sağlar. Önce tasarlama ve uygulama, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama önerilir doğrulayın:  
  
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
  
 Bu tür uygulamalar için bilgileri diğer platformlarda (dahil olmak üzere Microsoft dışı platformlar) iletmek için XML Hizmet sözleşmeleri genel olarak standart XML biçimlerde gibi belirtilmiştir [Web Hizmetleri Açıklama Dili (WSDL)](http://go.microsoft.com/fwlink/?LinkId=87004) ve [XML Şeması (XSD)](http://go.microsoft.com/fwlink/?LinkId=87005), diğerlerinin yanı sıra. Geliştiriciler için birçok platformda belirtimi dili anlamaları için hem dillere birlikte çalışabilirliği sağlamak için tasarlandığından hizmeti ile iletişim kurabilen uygulamaları oluşturmak için bu ortak sözleşme bilgilerini kullanabilirsiniz Genel form, biçimleri ve protokolleri hizmetini destekleyen açıklayarak. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]nasıl [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tanıtıcıları bilgi, bu tür bkz [meta verileri](../../../../docs/framework/wcf/feature-details/metadata.md).  
  
 Sözleşmeleri ifade edilir birçok yolu, ancak ve WSDL ve XSD Hizmetleri erişilebilir bir biçimde tanımlamak için mükemmel dilleri olsa da, bunlar doğrudan kullanılacak zor dilleri — yalnızca bir hizmet, değil hizmet sözleşmesi açıklamalarını oldukları herhangi bir durumda uygulamaları. Bu nedenle, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamalar, yönetilen öznitelikleri, arabirimleri ve sınıfları yapısını tanımlar ve bir hizmet uygulamak için kullanın.  
  
 Yönetilen türlerinde tanımlanan ortaya çıkan sözleşmeyi dönüştürülebilir (olarak da bilinir *dışarı*) meta veri olarak — WSDL ve XSD — istemciler veya diğer platformlarda özellikle diğer hizmet Implementers gerektiğinde. Sonuç herhangi bir istemci uygulama için ortak meta verileri kullanarak açıklanan basit bir programlama modelidir. Güvenlikle ilgili bilgiler ve taşıma gibi temel alınan SOAP iletilerine ayrıntılarını için bırakılabilir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], gerekli ve türlerinden dönüşümler hizmet sözleşmesi tür sistemi XML türü sistemine otomatik olarak gerçekleştirir.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]tasarlama sözleşmeleri görmek [Hizmet sözleşmeleri tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]sözleşmelerini uygulama, bkz: [hizmet sözleşmelerini uygulama](../../../../docs/framework/wcf/implementing-service-contracts.md).  
  
 Ayrıca, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Ayrıca hizmet sözleşmeleri ileti düzeyinde tamamen geliştirme olanağı sağlar. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]ileti düzeyinde geliştirme Hizmet sözleşmeleri bkz [kullanarak ileti sözleşmeleri](../../../../docs/framework/wcf/feature-details/using-message-contracts.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Geliştirme Hizmetleri içinde SOAP XML olmayan, bkz: [POX uygulamaları ile birlikte çalışabilirlik](../../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md).  
  
### <a name="understanding-the-hierarchy-of-requirements"></a>Gereksinimleri hiyerarşisini anlama  
 Bir hizmet sözleşmesini operations grupları; İleti türleri MEP belirtir ve bu iletileri taşıyan veri türleri; çalışma zamanı davranışını sözleşme desteklemek için bir uygulama olmalıdır kategorilerini belirtir (örneğin, iletileri imzalanmış ve şifrelenecek olduğunu gerektiren). Ancak, hizmet sözleşmesini kendisi, tam olarak nasıl bu gereksinimleri, yalnızca, olması gereken karşılandığından belirtmiyor. Hangi şifreleme veya nasıl bir ileti imzalı uygulama ve uyumlu bir hizmet yapılandırmasını kadar türüdür.  
  
 Sözleşme davranışı eklemek için belirli konular hizmet sözleşmesini uygulama ve çalışma zamanı yapılandırma gerektirir şekilde dikkat edin. Bir hizmeti kullanmak için kullanıma sunmak için karşılanması gereken gereksinimleri kümesi gereksinimleri önceki kümesinde oluşturur. Bir sözleşme uygulama gereksinimlerini yaparsa, bir uygulama henüz gerektirebilir için yapılandırma ve çalıştırmak hizmeti etkinleştirmek bağlamaları daha fazla. Son olarak, konak uygulama hizmet yapılandırması bağlamaları Ekle ve herhangi bir gereksinimi desteklemelidir.  
  
 Bu ek gereksinim işlem tasarlama, uygulama, yapılandırma ve barındırma çalışırken göz önünde bulundurmanız önemlidir, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmet uygulaması. Örneğin, sözleşmenin bir oturum desteklemek gerektiğini belirtebilirsiniz. Bu durumda, bağlama sözleşme bu gereksinimi desteklemek için yapılandırmanız gerekir ya da hizmet uygulaması çalışmaz. Veya hizmetinizi tümleşik Windows kimlik doğrulaması gerektiriyorsa ve Internet Information Services (IIS) barındırılan hizmetin bulunduğu Web uygulaması Tümleşik Windows kimlik doğrulaması açık ve kapalı anonim destek olması gerekir. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Özellikler ve farklı hizmet ana uygulama türleri etkisini görmek [barındırma](../../../../docs/framework/wcf/feature-details/hosting.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uç Noktalar: Adresler, Bağlamalar ve Anlaşmalar](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [Hizmet Sözleşmeleri Tasarlama](../../../../docs/framework/wcf/designing-service-contracts.md)  
 [Hizmet Anlaşmalarını Uygulama](../../../../docs/framework/wcf/implementing-service-contracts.md)
