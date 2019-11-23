---
title: Hizmetleri Tasarlama ve Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- defining service contracts [WCF]
ms.assetid: 036fae20-7c55-4002-b71d-ac4466e167a3
ms.openlocfilehash: 0d569d12b5bc555a07e94fa89c5a19f52f4a6b6c
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318396"
---
# <a name="designing-and-implementing-services"></a>Hizmetleri Tasarlama ve Uygulama
Bu bölümde, WCF sözleşmelerini tanımlama ve uygulama işlemlerinin nasıl yapılacağı gösterilir. Bir hizmet sözleşmesi, bir uç noktanın dış dünyaya ne iletişim kuracağını belirtir. Daha somut bir düzeyde, istek/yanıt, tek yönlü ve çift yönlü gibi temel ileti değişimi desenleri (MEPs) halinde düzenlenmiş belirli bir ileti kümesinin bir ifadesidir. Bir hizmet sözleşmesi mantıksal olarak ilişkili bir ileti değişimi kümesi ise, bir hizmet işlemi tek bir ileti alışverişi olur. Örneğin, bir `Hello` işlem, tek bir iletiyi kabul etmelidir (çağıranın selamlamayı duyurabilmesi) ve bir ileti döndürmeyebilir (işlemin ne olduğuna bağlı olarak).  
  
 Sözleşmeler ve diğer çekirdek Windows Communication Foundation (WCF) kavramları hakkında daha fazla bilgi için bkz. [temel Windows Communication Foundation kavramlar](fundamental-concepts.md). Bu konu, hizmet sözleşmelerini anlamak için odaklanır. Hizmetlere bağlanmak için hizmet sözleşmeleri kullanan istemciler oluşturma hakkında daha fazla bilgi için bkz. [WCF Istemcisine genel bakış](wcf-client-overview.md).  
  
## <a name="overview"></a>Genel bakış  
 Bu konuda, WCF Hizmetleri tasarlamak ve uygulamak için yüksek düzeyde kavramsal bir yön sağlanır. Alt konuları, tasarım ve uygulamanın özellikleri hakkında daha ayrıntılı bilgi sağlar. WCF uygulamanızı tasarlamaya ve uygulamadan önce şunları yapmanız önerilir:  
  
- Hizmet sözleşmesinin ne olduğunu, nasıl çalıştığını ve bir tane nasıl oluşturulacağını anlayın.  
  
- Sözleşmelerin durum, çalışma zamanı yapılandırması veya barındırma ortamının desteklemediği en düşük gereksinimleri anlayın.  
  
## <a name="service-contracts"></a>Hizmet Sözleşmeleri  
 Bir hizmet sözleşmesi şunları belirtir:  
  
- Bir sözleşmenin sunduğu işlemler.  
  
- Değiştirilen ileti bakımından işlemlerin imzası.  
  
- Bu iletilerin veri türleri.  
  
- İşlemlerin konumu.  
  
- Hizmetle başarılı iletişimi desteklemek için kullanılan belirli protokoller ve serileştirme biçimleri.  
  
 Örneğin, bir satınalma siparişi sözleşmesinin, sipariş bilgisi türlerinin bir girişini kabul eden ve bir sipariş tanımlayıcısı dahil olmak üzere başarı veya hata bilgilerini döndüren `CreateOrder` bir işlemi olabilir. Ayrıca, bir sıra tanımlayıcısını kabul eden ve sıra durum bilgilerini döndüren `GetOrderStatus` bir işlem olabilir. Bu sıralamanın bir hizmet sözleşmesi şunları belirtir:  
  
1. Satın alma siparişi sözleşmesinin `CreateOrder` ve `GetOrderStatus` işlemleri vardır.  
  
2. İşlemler giriş iletileri ve çıkış iletileri belirtti.  
  
3. Bu iletilerin taşıya, verileri.  
  
4. İletileri başarıyla işlemek için gereken iletişim altyapısına ilişkin kategorik deyimler. Örneğin, bu ayrıntılar başarılı bir iletişim kurmak için hangi güvenlik biçimlerinin gerekli olup olmayacağını ve bu ayrıntıları içerir.  
  
 Bu tür bilgileri pek çok platformda diğer uygulamalarla (Microsoft dışı platformlar dahil) iletmek için, XML hizmeti sözleşmeleri, diğer kullanıcıların yanı sıra [Web Hizmetleri Açıklama Dili](https://go.microsoft.com/fwlink/?LinkId=94952) (wsdl) ve [XML şeması](https://go.microsoft.com/fwlink/?LinkId=94953) (xsd) gibi standart XML biçimlerinde ifade edilir. Birçok platforma yönelik geliştiriciler, bu ortak sözleşme bilgilerini, her ikisi de belirtim dilini anladığından ve bu dillerin birlikte çalışabilirliği etkinleştirmek üzere tasarlandıkları için hizmetle iletişim kurabilen uygulamalar oluşturmak için kullanabilir. Hizmetin desteklediği ortak formları, biçimleri ve protokolleri açıklayarak. WCF 'nin bu tür bilgileri nasıl ele aldığı hakkında daha fazla bilgi için bkz. [metadata](./feature-details/metadata.md).  
  
 Sözleşmeler birçok yoldan ifade edilebilir, ancak WSDL ve XSD hizmetleri erişilebilir bir şekilde tanımlamaya yönelik harika diller olsa da, doğrudan kullanılması zor dillerdir ve hizmet sözleşmesi uygulamalarının sadece bir hizmet açıklamalarıdır. Bu nedenle, WCF uygulamaları bir hizmetin yapısını tanımlamak ve uygulamayı uygulamak için hem yönetilen öznitelikleri, arabirimleri hem de sınıfları kullanır.  
  
 Yönetilen türlerde tanımlanan sonuç sözleşmesi, istemciler veya diğer hizmet uygulayıcıları için gerektiğinde meta veriler (WSDL ve XSD) olarak *aktarılabilir* . Sonuç, herhangi bir istemci uygulamasına (ortak meta veriler kullanılarak) açıklanabilir ve basit bir programlama modelidir. Temel alınan SOAP iletilerinin ayrıntıları, ulaşım ve güvenlikle ilgili bilgiler, vb., hizmet sözleşmesi türü sistemine ve ' a yönelik gerekli dönüştürmeleri otomatik olarak XML türü sistemine uygulayan WCF 'ye bırakılabilir.  
  
 Sözleşmeleri tasarlama hakkında daha fazla bilgi için bkz. [hizmet sözleşmeleri tasarlama](designing-service-contracts.md). Sözleşmeleri uygulama hakkında daha fazla bilgi için bkz. [hizmet sözleşmelerini uygulama](implementing-service-contracts.md).  
  
### <a name="messages-up-front-and-center"></a>Ön ve Merkez iletileri  
 Yönetilen arabirimleri, sınıfları ve hizmet işlemlerini modellemek için yöntemleri kullanmak, uzak yordam çağrısı (RPC)-stil yöntemi imzalarında kullanıldığında, parametreleri bir yönteme geçirmek ve dönüş değerlerini almak için normal bir biçim olduğunda basittir. bir nesneden veya diğer kod türünden işlevsellik isteme. Örneğin, Visual Basic ve C++ com gibi yönetilen dilleri kullanan programcılar, RPC stili yaklaşım (nesnelerin veya arabirimlerin kullanılması), RPC stili dağıtılan nesne sistemlerinde bulunan sorunları yaşamaya gerek kalmadan WCF hizmeti sözleşmeleri oluşturulmasına neden olabilir. Hizmet yönü, esnek olarak bağlanmış, ileti yönelimli bir programlamanın sağladığı avantajlardan yararlanır ve bu sayede RPC programlama deneyiminin kolaylığını ve bu deneyimin kullanımını korur.  
  
 Birçok programcı, Microsoft MSMQ gibi ileti kuyrukları, .NET Framework <xref:System.Messaging> ad alanları veya HTTP isteklerinde yapılandırılmamış XML gönderirken birkaç kez daha rahat hale getirilmektedir. İleti düzeyinde programlama hakkında daha fazla bilgi için bkz. [POX uygulamalarıyla](./feature-details/interoperability-with-pox-applications.md) [İleti sözleşmeleri](./feature-details/using-message-contracts.md), [hizmet kanalı düzeyi programlama](./extending/service-channel-level-programming.md)ve birlikte çalışabilirliği kullanma.  
  
### <a name="understanding-the-hierarchy-of-requirements"></a>Gereksinimlerin hiyerarşisini anlama  
 Bir hizmet sözleşmesi işlemleri gruplandırır; ileti değişim modelini, ileti türlerini ve bu iletilerin hangi veri türlerini taşımakta olduğunu belirtir; Ayrıca, bir uygulamanın sözleşmeyi desteklemek için sahip olması gereken çalışma zamanı davranışının kategorilerini gösterir (örneğin, iletilerin şifrelenmesini ve imzalanmasını gerektirebilir). Hizmet sözleşmesinin kendisi, bu gereksinimlerin nasıl karşılandığını tam olarak belirtmez, yalnızca bunların olması gerekir. Şifreleme türü veya bir iletinin imzalandığı yol, uyumlu bir hizmetin uygulamasına ve yapılandırmasına kadar.  
  
 Sözleşmenin, hizmet sözleşmesi uygulamasının belirli şeyleri ve davranış eklemesi için çalışma zamanı yapılandırmasını gerektirdiğini fark edebilirsiniz. Bir hizmeti önceki gereksinimler kümesinde kullanım derlemeleri için kullanıma sunmak üzere karşılanması gereken gereksinimler kümesi. Bir sözleşme uygulamanın gereksinimlerini yapıyorsa, bir uygulama hizmetin çalışmasına imkan tanıyan yapılandırma ve bağlamalardan daha fazlasını gerektirebilir. Son olarak, ana bilgisayar uygulaması hizmet yapılandırmasının ve bağlamaların eklemesi gereken tüm gereksinimleri de desteklemelidir.  
  
 Bu ek gereksinim süreci, bir Windows Communication Foundation (WCF) hizmet uygulamasını tasarlarken, uygularken, yapılandırırken ve barındırırken göz önünde bulundurmanız önemlidir. Örneğin, sözleşme, bir oturumu desteklemesi gerektiğini belirtebilir. Bu durumda, bu, sözleşmeli gereksinimi destekleyecek şekilde bağlamayı yapılandırmanız veya hizmet uygulamasının çalışmamaları gerekir. Ya da hizmetiniz Windows tümleşik kimlik doğrulaması gerektiriyorsa ve Internet Information Services (IIS) içinde barındırılıyorsa, hizmetin bulunduğu Web uygulamasında Windows tümleşik kimlik doğrulamasının açık olması ve anonim desteğin kapalı olması gerekir. Farklı hizmet ana bilgisayarı uygulama türlerinin özellikleri ve etkileri hakkında daha fazla bilgi için bkz. [barındırma hizmetleri](hosting-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmet Sözleşmeleri Tasarlama](designing-service-contracts.md)
- [Hizmet Anlaşmalarını Uygulama](implementing-service-contracts.md)
