---
title: Sözleşmeler
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], contracts
- contracts [WCF]
- Windows Communication Foundation [WCF], contracts
ms.assetid: c8364183-4ac1-480b-804a-c5e6c59a5d7d
ms.openlocfilehash: 1cd7e54d50e7116c71c040df1965674a4fdaff13
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595602"
---
# <a name="contracts"></a>Sözleşmeler
Bu bölümde Windows Communication Foundation (WCF) sözleşmelerini tanımlama ve uygulama işlemlerinin nasıl tanımlanacağı gösterilmektedir. Bir hizmet sözleşmesi, bir uç noktanın dış dünyaya ne iletişim kuracağını belirtir. Daha somut bir düzeyde, istek/yanıt, tek yönlü ve çift yönlü gibi temel ileti değişimi desenleri (MEPs) halinde düzenlenmiş belirli bir ileti kümesinin bir ifadesidir. Bir hizmet sözleşmesi mantıksal olarak ilişkili bir ileti değişimi kümesi ise, bir hizmet işlemi tek bir ileti alışverişi olur. Örneğin, bir `Hello` işlem, tek bir ileti kabul etmelidir (çağıranın selamlamayı duyurabilmesi için) ve bir ileti döndürmeyebilir (işlemin ne olduğuna bağlı olarak).  
  
 Sözleşmeler ve diğer temel WCF kavramları hakkında daha fazla bilgi için bkz. [temel Windows Communication Foundation kavramları](../fundamental-concepts.md). Bu konu, hizmet sözleşmelerini anlamak için odaklanır. Hizmetlere bağlanmak için hizmet sözleşmeleri kullanan istemciler oluşturma hakkında daha fazla bilgi için bkz. [WCF Istemcisine genel bakış](../wcf-client-overview.md). İstemci kanalları, istemci mimarisi ve diğer istemci sorunları hakkında daha fazla bilgi için bkz. [istemciler](clients.md).  
  
## <a name="overview"></a>Genel Bakış  
 Bu konuda, WCF Hizmetleri tasarlamak ve uygulamak için üst düzey kavramsal bir yön sağlanır. Alt konuları tasarlama ve uygulamanın özellikleri hakkında daha ayrıntılı bilgi sağlar. WCF uygulamanızı tasarlamaya ve uygulamadan önce şunları yapmanız önerilir:  
  
- Hizmet sözleşmesinin ne olduğunu, nasıl çalıştığını ve bir tane nasıl oluşturulacağını anlayın.  
  
- Sözleşmelerin durum en düşük gereksinimlerinin, çalışma zamanı yapılandırması veya barındırma ortamının destekleyebileceğini anlayın.  
  
## <a name="service-contracts"></a>Hizmet Sözleşmeleri  
 Hizmet sözleşmesi, hakkında bilgi sağlayan bir ifadedir:  
  
- Bir hizmette işlem gruplandırması.  
  
- Değiştirilen ileti bakımından işlemlerin imzası.  
  
- Bu iletilerin veri türleri.  
  
- İşlemlerin konumu.  
  
- Hizmetle başarılı iletişimi desteklemek için kullanılan belirli protokoller ve serileştirme biçimleri.  
  
 Örneğin, bir satın alma siparişi sözleşmesi, `CreateOrder` sipariş bilgisi türlerinin bir girişini kabul eden ve bir sipariş tanımlayıcısı dahil olmak üzere başarı veya başarısızlık bilgilerini döndüren bir işleme sahip olabilir. Ayrıca, `GetOrderStatus` bir sıra tanımlayıcısı kabul eden ve sipariş durum bilgilerini döndüren bir işlemi olabilir. Bu sıralamanın bir hizmet sözleşmesi şunları belirtir:  
  
- Satın alma siparişi sözleşmesinin, `CreateOrder` ve işlemleri tarafından hesaplandığı `GetOrderStatus` .  
  
- İşlemler giriş iletileri ve çıkış iletileri belirtti.  
  
- Bu iletilerin taşıya, verileri.  
  
- İletileri başarıyla işlemek için gereken iletişim altyapısına ilişkin kategorik deyimler. Örneğin, bu ayrıntılar başarılı bir iletişim kurmak için hangi güvenlik biçimlerinin gerekli olup olmayacağını ve bu ayrıntıları içerir.  
  
 Bu tür bilgileri diğer platformlardaki uygulamalarla (Microsoft dışı platformlar dahil) iletmek için, XML hizmet sözleşmeleri, diğerleri arasında [Web Hizmetleri Açıklama Dili (wsdl)](https://www.w3.org/TR/2001/NOTE-wsdl-20010315) ve [XML şeması (xsd)](https://www.w3.org/XML/Schema)gibi standart XML biçimlerinde genel olarak ifade edilir. Birçok platforma yönelik geliştiriciler, bu ortak sözleşme bilgilerini, her ikisi de belirtim dilini anladığından ve bu dillerin hizmetin desteklediği ortak formları, biçimleri ve protokolleri açıklayarak birlikte çalışabilirlik sağlamak üzere tasarlandıklarından, hizmetle iletişim kurabilen uygulamalar oluşturmak için kullanabilir. WCF 'nin bu tür bilgileri nasıl ele aldığı hakkında daha fazla bilgi için bkz. [metadata](metadata.md).  
  
 Sözleşmeler, ancak, WSDL ve XSD hizmetleri erişilebilir bir şekilde ifade etmek için çok çeşitli yollarla ifade edilebilir, ancak her durumda, yalnızca bir hizmetin açıklamalarıdır. Bu nedenle, WCF uygulamaları, bir hizmeti uygulamak ve yapısını tanımlamak için hem yönetilen öznitelikleri, arabirimleri hem de sınıfları kullanır.  
  
 Yönetilen türlerde tanımlanan sonuç sözleşmesi, özellikle diğer platformlarda istemciler veya diğer hizmet uygulayıcıları tarafından gerektiğinde, WSDL ve XSD meta verileri *(adlandırılmış olarak*da bilinir) olarak dönüştürülebilirler. Sonuç, tüm istemci uygulamaları için genel meta verileri kullanarak açıklanabileceğinden, basit bir programlama modelidir. Taşıma ve güvenlikle ilgili bilgiler gibi temel alınan SOAP iletilerinin ayrıntıları, hizmet sözleşmesi türü sistemine ve otomatik olarak XML türü sistemine gereken dönüştürmeleri otomatik olarak gerçekleştiren WCF 'ye bırakılabilir.  
  
 Sözleşmeleri tasarlama hakkında daha fazla bilgi için bkz. [hizmet sözleşmeleri tasarlama](../designing-service-contracts.md). Sözleşmeleri uygulama hakkında daha fazla bilgi için bkz. [hizmet sözleşmelerini uygulama](../implementing-service-contracts.md).  
  
 Ayrıca, WCF Ayrıca hizmet sözleşmelerini tamamen ileti düzeyinde geliştirme yeteneği de sağlar. İleti düzeyinde hizmet sözleşmeleri geliştirme hakkında daha fazla bilgi için bkz. [Ileti sözleşmelerini kullanma](using-message-contracts.md). SOAP olmayan XML 'de hizmet geliştirme hakkında daha fazla bilgi için bkz. [POX Uygulamaları Ile birlikte çalışabilirlik](interoperability-with-pox-applications.md).  
  
### <a name="understanding-the-hierarchy-of-requirements"></a>Gereksinimlerin hiyerarşisini anlama  
 Bir hizmet sözleşmesi işlemleri gruplandırır; Bu iletilerin taşımakta olduğu MEP, ileti türleri ve veri türlerini belirtir; Ayrıca, bir uygulamanın sözleşmeyi desteklemek için sahip olması gereken çalışma zamanı davranışının kategorilerini gösterir (örneğin, iletilerin şifrelenmesini ve imzalanmasını gerektirebilir). Ancak, hizmet sözleşmesinin kendisi bu gereksinimlerin nasıl karşılandığını kesin bir şekilde belirtmez, yalnızca bunların olması gerekir. Hangi tür şifreleme veya bir iletinin imzalandığı, uyumlu bir hizmetin uygulamasına ve yapılandırmasına nasıl yapılır?  
  
 Sözleşmenin, hizmet sözleşmesi uygulamasının belirli şeyleri ve davranış eklemesi için çalışma zamanı yapılandırmasını gerektirdiğini fark edebilirsiniz. Bir hizmeti önceki gereksinimler kümesinde kullanım derlemeleri için kullanıma sunmak üzere karşılanması gereken gereksinimler kümesi. Bir sözleşme uygulamanın gereksinimlerini yapıyorsa, bir uygulama hizmetin çalışmasına imkan tanıyan yapılandırma ve bağlamalardan daha fazlasını gerektirebilir. Son olarak, ana bilgisayar uygulaması hizmet yapılandırmasının ve bağlamaların eklemesi gereken tüm gereksinimleri de desteklemelidir.  
  
 Bu ek gereksinim süreci, Windows Communication Foundation (WCF) hizmet uygulamanızı tasarlarken, uygularken, yapılandırırken ve barındırırken göz önünde bulundurmanız önemlidir. Örneğin, sözleşme, bir oturumu desteklemesi gerektiğini belirtebilir. Bu durumda, bu, sözleşmeli gereksinimi destekleyecek şekilde bağlamayı yapılandırmanız veya hizmet uygulamasının çalışmamaları gerekir. Ya da hizmetiniz tümleşik Windows kimlik doğrulaması gerektiriyorsa ve Internet Information Services (IIS) içinde barındırılıyorsa, hizmetin bulunduğu Web uygulamasının tümleşik Windows kimlik doğrulamasının açık olması ve anonim desteğinin kapalı olması gerekir. Farklı hizmet ana bilgisayarı uygulama türlerinin özellikleri ve etkileri hakkında daha fazla bilgi için bkz. [barındırma](hosting.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uç Noktalar: Adresler, Bağlamalar ve Anlaşmalar](endpoints-addresses-bindings-and-contracts.md)
- [Hizmet Sözleşmeleri Tasarlama](../designing-service-contracts.md)
- [Hizmet Sözleşmelerini Uygulama](../implementing-service-contracts.md)
