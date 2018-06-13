---
title: Hizmetleri Tasarlama ve Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- defining service contracts [WCF]
ms.assetid: 036fae20-7c55-4002-b71d-ac4466e167a3
ms.openlocfilehash: d4d4fb3600a25f05865dd56c220e7a8ade246f08
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33805073"
---
# <a name="designing-and-implementing-services"></a>Hizmetleri Tasarlama ve Uygulama
Bu bölümde tanımlayın ve WCF sözleşmeleri uygulamak gösterilmektedir. Bir hizmet sözleşmesini ne bir uç nokta için dış dünya iletişim kurar belirtir. Daha somut bir düzeyde, bu temel ileti exchange desenleri (MEPs) düzenlenmiştir belirli iletileri kümesi hakkında istek/yanıt gibi tek yönlü ve çift yönlü açıklamadır. Bir hizmet sözleşmesini ileti alışverişlerinde mantıksal olarak ilişkili bir dizi, bir hizmet işlemi tek bir ileti exchange ise. Örneğin, bir `Hello` işlemi (arayan Tebrik Duyurusu şekilde) açıkça bir ileti kabul etmeniz gerekir ve olabilir veya (işlemi geçici kullanım bağlı olarak) bir ileti döndürmeyebilir.  
  
 Sözleşmeler ve diğer temel Windows Communication Foundation (WCF) kavramlar hakkında daha fazla bilgi için bkz: [temel Windows Communication Foundation kavramları](../../../docs/framework/wcf/fundamental-concepts.md). Bu konu, hizmet sözleşmelerini anlamaya odaklanır. Hizmet sözleşmeleri hizmetlerine bağlanmak için kullanan istemciler oluşturma hakkında daha fazla bilgi için bkz: [WCF istemcisi genel bakış](../../../docs/framework/wcf/wcf-client-overview.md).  
  
## <a name="overview"></a>Genel Bakış  
 Bu konu, WCF hizmetleri tasarlama ve uygulama için bir üst düzey kavramsal yönlendirmesini sağlar. Konuları tasarım ve uygulama özellikleri hakkında daha ayrıntılı bilgi sağlar. Tasarlama ve WCF uygulamanızın uygulama önce önerilen doğrulayın:  
  
-   Anlamak hizmet sözleşmesini ne olduğu, nasıl çalıştığı ve nasıl oluşturulacağı.  
  
-   Sözleşmeleri en düşük gereksinimler durumunu anlamak, çalışma zamanı yapılandırma veya barındırma ortamı desteklemiyor.  
  
## <a name="service-contracts"></a>Hizmet Sözleşmeleri  
 Bir hizmet sözleşmesini aşağıdaki belirtir:  
  
-   Bir sözleşme işlemleri gösterir.  
  
-   Değiştirilen iletilerin açısından işlemleri imzası.  
  
-   Bu iletileri veri türleri.  
  
-   Operations konumu.  
  
-   Belirli protokolleri ve hizmeti ile başarılı iletişimi desteklemek için kullanılan serileştirme biçimleri.  
  
 Örneğin, bir satın alma siparişi sözleşme olabilir bir `CreateOrder` bir giriş sırası bilgilerinin kabul işlemi türleri ve bir sıra tanımlayıcısını dahil olmak üzere, başarı veya başarısızlık bilgileri döndürür. Ayrıca olabilir bir `GetOrderStatus` sipariş tanımlayıcı kabul edip sipariş durum bilgilerini döndürür işlemi. Bu tür bir hizmet sözleşmesini belirtmeniz gerekir:  
  
1.  Satın alma siparişi sözleşme, oluşmuştur `CreateOrder` ve `GetOrderStatus` işlemleri.  
  
2.  Operations belirttiğiniz iletileri giriş ve ileti çıkışı.  
  
3.  Bu iletiler taşıyabilir veriler.  
  
4.  Kategorik deyimleri başarıyla iletileri işlemek için gerekli iletişimini altyapısıyla ilgili. Örneğin, bu ayrıntıları dahil olup olmadığını ve hangi forms güvenlik başarıyla iletişim kurabilmek için sahip gereklidir.  
  
 Bu tür birçok platformda (dahil olmak üzere Microsoft dışı platformlar) diğer uygulamalara yönelik bilgileri iletmek için XML Hizmet sözleşmeleri genel olarak standart XML biçimlerde gibi belirtilmiştir [Web Hizmetleri Açıklama Dili](http://go.microsoft.com/fwlink/?LinkId=94952) () WSDL) ve [XML Şeması](http://go.microsoft.com/fwlink/?LinkId=94953) (XSD), diğerlerinin yanı sıra. Geliştiriciler için birçok platformda belirtimi dili anlamaları için hem dillere birlikte çalışabilirliği sağlamak için tasarlandığından hizmeti ile iletişim kurabilen uygulamaları oluşturmak için bu ortak sözleşme bilgilerini kullanabilirsiniz Genel form, biçimleri ve protokolleri hizmetini destekleyen açıklayarak. WCF bu tür bilgileri nasıl işlediği hakkında daha fazla bilgi için bkz: [meta verileri](../../../docs/framework/wcf/feature-details/metadata.md).  
  
 Sözleşmeleri birçok yolu ifade edilebilir ve WSDL ve XSD Hizmetleri erişilebilir bir biçimde tanımlamak için mükemmel dilleri olsa da, bunlar doğrudan kullanılacak zor diller ve yalnızca bir hizmet, hizmet sözleşmesi uygulamaları açıklamaları. Bu nedenle, WCF uygulamaları hizmet yapısını tanımlar ve uygulamak için yönetilen öznitelikleri, arabirimleri ve sınıfları kullanın.  
  
 Yönetilen türlerinde tanımlanan ortaya çıkan sözleşmeyi olabilir *dışarı* meta veri olarak — WSDL ve XSD — istemcileri veya diğer hizmet Implementers tarafından gerektiğinde. Sonuç (ortak meta verileri kullanarak) açıklanan basit bir programlama modeli, için tüm istemci uygulamasıdır. Temel alınan SOAP iletilerine, taşıma ve güvenlikle ilgili bilgileri ve benzeri ayrıntılarını gerekli ve türlerinden dönüşümler hizmet sözleşmesi tür sistemi XML türü sistemine otomatik olarak gerçekleştirir WCF bırakılabilir.  
  
 Sözleşmeleri tasarlama hakkında daha fazla bilgi için bkz: [Hizmet sözleşmeleri tasarlama](../../../docs/framework/wcf/designing-service-contracts.md). Sözleşmelerini uygulama hakkında daha fazla bilgi için bkz: [hizmet sözleşmelerini uygulama](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
### <a name="messages-up-front-and-center"></a>Ön ve merkezi iletileri  
 Yönetilen arabirimleri, sınıflar ve yöntemler modeli hizmet işlemlerine kullanarak basit uzaktan yordam çağrısı (RPC) kullanıldığında-stil yöntemi imzalar, hangi bir yönteme parametreleri geçirme dönüş değerleri alma olup normal biçiminde bir nesne veya başka bir kod türünden işlevselliği isteniyor. Örneğin, Visual Basic ve C++ COM gibi yönetilen dilleri kullanarak programcıları bilgilerini RPC-style yaklaşımın (nesneleri veya arabirimleri kullanarak olup olmadığını) WCF hizmet sözleşmeleri oluşturulmasını ndaki sorunları almadan uygulayabilirsiniz Dağıtılmış nesne sistemleri RPC stili. Hizmet yönlendirmesi programlama deneyimine kolaylığı ve RPC aşina olduğunuz korurken geniş eşleşmiş, ileti kaynaklı programlama yararları sağlar.  
  
 İleti kaynaklı uygulama programlama arabirimleri, Microsoft MSMQ gibi ileti kuyrukları gibi birçok Programcı daha rahat <xref:System.Messaging> .NET Framework veya HTTP istekleri gönderen yapılandırılmamış XML ad alanları. İleti düzeyinde programlama hakkında daha fazla bilgi için bkz: [kullanarak ileti sözleşmeleri](../../../docs/framework/wcf/feature-details/using-message-contracts.md), [hizmet kanal düzeyi programlama](../../../docs/framework/wcf/extending/service-channel-level-programming.md), ve [POXuygulamalarıilebirlikteçalışabilirlik](../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md).  
  
### <a name="understanding-the-hierarchy-of-requirements"></a>Gereksinimleri hiyerarşisini anlama  
 Bir hizmet sözleşmesini operations grupları; ileti değişim deseni, ileti türleri ve veri türleri bu iletileri taşıyan belirtir; çalışma zamanı davranışını sözleşme desteklemek için bir uygulama olmalıdır kategorilerini belirtir (örneğin, iletileri imzalanmış ve şifrelenecek olduğunu gerektiren). Hizmet sözleşmesi tam olarak nasıl bu gereksinimleri, yalnızca, olması gereken karşılandığından belirtmiyor. Şifreleme veya bir ileti imzalanmış şekilde en fazla uygulama ve uyumlu bir hizmet yapılandırmasını türüdür.  
  
 Sözleşme davranışı eklemek için belirli konular hizmet sözleşmesini uygulama ve çalışma zamanı yapılandırma gerektirir şekilde dikkat edin. Bir hizmeti kullanmak için kullanıma sunmak için karşılanması gereken gereksinimleri kümesi gereksinimleri önceki kümesinde oluşturur. Bir sözleşme uygulama gereksinimlerini yaparsa, bir uygulama henüz gerektirebilir için yapılandırma ve çalıştırmak hizmeti etkinleştirmek bağlamaları daha fazla. Son olarak, konak uygulama hizmet yapılandırması bağlamaları Ekle ve herhangi bir gereksinimi desteklemelidir.  
  
 Bu ek gereksinim işlem tasarlama, uygulama, yapılandırma ve bir Windows Communication Foundation (WCF) hizmeti uygulamasını barındıran çalışırken göz önünde bulundurmanız önemlidir. Örneğin, sözleşmenin bir oturum desteklemek gerektiğini belirtebilirsiniz. Bu durumda, bağlama sözleşme bu gereksinimi desteklemek için yapılandırmanız gerekir ya da hizmet uygulaması çalışmaz. Veya hizmet Windows tümleşik kimlik doğrulaması gerektiriyorsa ve Internet Information Services (IIS) barındırılan hizmetin bulunduğu Web uygulaması Windows tümleşik kimlik açık ve kapalı anonim destek olması gerekir. Farklı hizmet ana uygulama türleri etkisini ve özellikler hakkında daha fazla bilgi için bkz: [barındırma hizmetleri](../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hizmet Sözleşmeleri Tasarlama](../../../docs/framework/wcf/designing-service-contracts.md)  
 [Hizmet Anlaşmalarını Uygulama](../../../docs/framework/wcf/implementing-service-contracts.md)
