---
title: Hizmetleri Tasarlama ve Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- defining service contracts [WCF]
ms.assetid: 036fae20-7c55-4002-b71d-ac4466e167a3
ms.openlocfilehash: ad7e713ac4cbbe5bf227f4ab93e8f88684dcb0d3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785027"
---
# <a name="designing-and-implementing-services"></a>Hizmetleri Tasarlama ve Uygulama
Bu bölümde tanımlaması ve WCF sözleşmeleri gösterilmektedir. Ne bir uç nokta için dış dünya iletişim kuran bir hizmet sözleşmesi belirler. Daha somut bir düzeyde istek/yanıt gibi tek yönlü ve çift yönlü bir dizi temel ileti exchange desenleri (MEPs) ile düzenlenmiş belirli ileti hakkında bir deyim olduğu. Bir hizmet sözleşmesini ileti alışverişlerinde mantıksal olarak ilişkili bir dizi ise, bir hizmet işlemi bir tek ileti alışverişi olur. Örneğin, bir `Hello` işlemi (arayan Karşılama duyurmaktan biçimde) bir ileti açıkça kabul etmelidir ve olabilir veya (işlemin ilgili bağlı olarak) bir ileti döndürmeyebilir.  
  
 Sözleşmeler ve diğer temel Windows Communication Foundation (WCF) kavramları hakkında daha fazla bilgi için bkz. [temel Windows Communication Foundation kavramları](../../../docs/framework/wcf/fundamental-concepts.md). Bu konu başlığı altında hizmet sözleşmelerini anlamaya odaklanır. Hizmet sözleşmeleri hizmetlerine bağlanmak için kullanan istemciler oluşturma hakkında daha fazla bilgi için bkz. [WCF istemcisi genel bakış](../../../docs/framework/wcf/wcf-client-overview.md).  
  
## <a name="overview"></a>Genel Bakış  
 Bu konu, WCF hizmetleri tasarlama ve uygulama için bir üst düzey kavramsal yönlendirme sağlar. Alt konuları, tasarım ve uygulama özellikleri hakkında daha ayrıntılı bilgi sağlar. Tasarlama ve uygulama WCF uygulamanızı önce önerilen aldığınız:  
  
- Anlamak hizmet sözleşmesini ne olduğu, nasıl çalıştığını ve nasıl oluşturacağınızı.  
  
- Sözleşmeler en düşük gereksinimleri durumunu anlamak, çalışma zamanı yapılandırma veya barındırma ortamı değil destekleyebilir.  
  
## <a name="service-contracts"></a>Hizmet Sözleşmeleri  
 Bir hizmet sözleşmesini aşağıdaki belirtir:  
  
- Bir sözleşme işlemleri sunar.  
  
- İşlem iletileri değiş tokuş imzası.  
  
- Bu iletileri veri türleri.  
  
- İşlemleri konumu.  
  
- Başarılı iletişim hizmetiyle desteklemek için kullanılan serileştirme biçimleri ve belirli protokoller.  
  
 Örneğin, bir satın alma siparişi sözleşme olabilir bir `CreateOrder` sipariş bilgileri bir girişi kabul eden bir işlem türleri ve siparişi tanımlayıcısı dahil olmak üzere, başarı veya başarısızlık durumu bilgilerini döndürür. Ayrıca olabilir bir `GetOrderStatus` işlemi, bir siparişi tanımlayıcısı kabul eden ve sipariş durumu bilgilerini döndürür. Bu tür bir hizmet sözleşmesini belirtmeniz gerekir:  
  
1. Satın alma siparişi sözleşme, toplamda `CreateOrder` ve `GetOrderStatus` operations.  
  
2. İşlemleri belirttiğiniz iletileri giriş ve çıkış iletileri.  
  
3. Bu iletiler gerçekleştirebilirsiniz veriler.  
  
4. Kategorik deyimleri hakkında iletişim altyapısı başarıyla iletileri işlemek için gerekli. Örneğin, bu Ayrıntılar arasında olup olmadığını ve hangi güvenlik formları başarılı iletişim kurmak için gereklidir.  
  
 Bu tür birçok platformda (Microsoft olmayan platformlar dahil) diğer uygulamalara yönelik bilgileri iletmek için XML hizmet sözleşmelerini herkese açık şekilde standart XML biçimlerde, gibi ifade edilir [Web Hizmetleri Açıklama Dili](https://go.microsoft.com/fwlink/?LinkId=94952) () WSDL) ve [XML Şeması](https://go.microsoft.com/fwlink/?LinkId=94953) (XSD), diğerlerinin yanı sıra. Geliştiriciler için birçok platformda dil belirtiminin anladıkları olduğundan hem dillere birlikte çalışabilirliği etkinleştirmek için tasarlandığından hizmet ile iletişim kurabilen uygulamaları oluşturmak için bu genel sözleşme bilgileriniz kullanabilirsiniz Genel form, biçimleri ve protokolleri hizmetinin desteklediği açıklayarak. WCF bu tür bilgileri nasıl işlediği hakkında daha fazla bilgi için bkz. [meta verileri](../../../docs/framework/wcf/feature-details/metadata.md).  
  
 Sözleşmeler birçok yolu belirtilebilir ve WSDL ve XSD Hizmetleri erişilebilir bir şekilde tanımlamak için mükemmel dilleri olsa da, bunlar doğrudan kullanmak zor diller ve yalnızca bir hizmetin hizmet sözleşme uygulamaları açıklamalardır. Bu nedenle, WCF uygulamaları hizmet yapısını tanımlamak ve uygulamak için yönetilen öznitelikleri, arabirimler ve sınıflar kullanın.  
  
 Yönetilen türler tanımlanan elde edilen anlaşma olabilir *dışarı* meta veri olarak — WSDL ve XSD — istemcileri veya diğer hizmet uygulayıcılar tarafından gerektiğinde. Sonuç, tüm istemci uygulamaları için (genel meta verileri kullanarak) açıklanan basit bir programlama modeli olur. Temel alınan SOAP iletilerini, nakliye ve güvenlikle ilgili bilgiler ve benzeri ayrıntılarını gerekli ve türlerinden dönüşümler hizmet sözleşme tür sistemi XML türü sistemine otomatik olarak gerçekleştirir WCF bırakılabilir.  
  
 Sözleşmeleri tasarlama hakkında daha fazla bilgi için bkz. [Hizmet sözleşmeleri tasarlama](../../../docs/framework/wcf/designing-service-contracts.md). Sözleşmelerini uygulama hakkında daha fazla bilgi için bkz. [hizmet sözleşmelerini uygulama](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
### <a name="messages-up-front-and-center"></a>Merkezi iletileri  
 Yönetilen arabirimler, sınıflar ve yöntemler modeli hizmet işlemlerine kullanmaktır basit uzaktan yordam çağrısı (RPC) kullanıldığında-yöntem imzaları hangi bir yönteme parametre geçirme ve dönüş değerleri alma içinde olan normal biçimini, stili işlevi, bir nesne veya başka bir kod türünden isteniyor. Örneğin, Visual Basic ve C++ COM gibi yönetilen dilleri kullanarak programcılar RPC stili yaklaşımın bilgilerini (nesneler veya arabirimleri kullanılarak olup olmadığını) WCF hizmet sözleşmelerini oluşturulmasını ndaki sorunları yaşayan olmadan uygulayabilirsiniz Dağıtılmış nesne sistemleri RPC stili. Hizmet yönlendirmesi kolaylığı ve aşina olduğunuz RPC korurken gevşek, ileti kaynaklı programlama avantajlarını programlama deneyimi sağlar.  
  
 İleti kaynaklı uygulama programlama arabirimleri, ileti kuyrukları gibi Microsoft MSMQ gibi birçok Programcı daha rahat <xref:System.Messaging> .NET Framework veya HTTP istekleri gönderen yapılandırılmamış XML'de ad alanları. İleti düzeyi programlama hakkında daha fazla bilgi için bkz: [kullanarak ileti sözleşmeleri](../../../docs/framework/wcf/feature-details/using-message-contracts.md), [hizmet kanal düzeyi programlama](../../../docs/framework/wcf/extending/service-channel-level-programming.md), ve [POXuygulamalarıilebirlikteçalışabilirlik](../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md).  
  
### <a name="understanding-the-hierarchy-of-requirements"></a>Hiyerarşi gereksinimlerini anlama  
 Bir hizmet sözleşmesini işlemleri grupları; ileti değişim deseni, ileti türleri ve veri türleri bu iletileri carry belirtir. çalışma zamanı davranışını uygulama destek sözleşmesi olmalıdır kategorilerini belirtir (örneğin, iletileri imzalı şifrelenir ve gerekli olabilir). Hizmet sözleşmesi, tam olarak nasıl Bu gereksinimler, yalnızca, olması gereken karşılandığından belirtmiyor. Şifreleme ya da bir ileti imzalandığı şekilde en fazla uygulama ve uyumlu bir hizmet yapılandırmasını türüdür.  
  
 Sözleşme davranış eklemek için belirli şeyleri hizmet sözleşmesi uygulama ve çalışma zamanı yapılandırma gerektiren şekilde dikkat edin. Önceki gereksinimler kümesine kullanmak için bir hizmeti kullanıma sunmak için karşılanması gereken gereksinimleri kümesini oluşturur. Bir sözleşme uygulama gereksinimlerini yaparsa, bir uygulama henüz gerektirebilir daha fazla çalıştırmak hizmet bağlamaları ve yapılandırma. Son olarak, ana bilgisayar uygulaması hizmet yapılandırması ve bağlamalar eklemek gereksinimlere desteklemelidir.  
  
 Bu ek gereksinim işlem tasarlama, uygulama, yapılandırma ve bir Windows Communication Foundation (WCF) hizmeti uygulamasını barındıran çalışırken göz önünde bulundurmanız önemlidir. Örneğin, sözleşmenin bir oturumu desteklemek gerektiğini belirtebilirsiniz. Bu durumda, sözleşmeye dayalı bu gereksinimi desteklemek için bağlama yapılandırmanız gerekir ya da hizmet uygulamasında çalışmaz. Ya da Hizmetiniz Windows tümleşik kimlik doğrulaması gerektirir ve Internet Information Services (IIS) barındırılan hizmetin içinde bulunduğu Web uygulaması Windows tümleşik kimlik açık ve kapalı anonim destek sahip olmanız gerekir. Farklı hizmet konak uygulama türleri etkisini ve özellikleri hakkında daha fazla bilgi için bkz. [barındırma hizmetleri](../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmet Sözleşmeleri Tasarlama](../../../docs/framework/wcf/designing-service-contracts.md)
- [Hizmet Anlaşmalarını Uygulama](../../../docs/framework/wcf/implementing-service-contracts.md)
