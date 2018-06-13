---
title: Windows Communication Foundation nedir?
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], technology overview
- technology overview [WCF]
- WCF [WCF], technology overview
ms.assetid: 40e1009d-ef15-450b-9848-62eabe5e5738
ms.openlocfilehash: e49b393b9dd09a513066a6cb3612ad9f938e9adb
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807423"
---
# <a name="what-is-windows-communication-foundation"></a>Windows Communication Foundation nedir?
Windows Communication Foundation (WCF) hizmet odaklı uygulamalar oluşturmaya yönelik bir çerçevedir. WCF kullanarak verileri zaman uyumsuz ileti bir hizmet uç noktasından diğerine gönderebilirsiniz. Hizmet uç noktası, IIS tarafından barındırılan sürekli olarak kullanılabilir bir hizmetin parçası veya bir uygulamada barındırılan bir hizmete olabilir. Bir uç nokta veri Hizmeti uç noktasından ister bir hizmetin istemci olabilir. İletileri tek karakter veya XML olarak gönderilen sözcük kadar basit ya da bir ikili veri akışı kadar karmaşık olabilir. Bazı örnek senaryolar şunlardır:  
  
-   İş işlemleri için güvenli bir hizmet.  
  
-   Bir trafik rapor veya diğer izleme hizmeti gibi başkalarına, geçerli veri sağlayan bir hizmet.  
  
-   İletişim veya gerçek zamanlı veri değişimi iki kişinin sağlayan bir sohbet hizmeti.  
  
-   Bir veya daha fazla yoklar bir Pano uygulaması için Veri Hizmetleri ve bir mantıksal sunuya sunar.  
  
-   WCF hizmet olarak Windows Workflow Foundation kullanılarak uygulanan bir iş akışı gösterme.  
  
-   Bir hizmet için en yeni verileri yoklamak için Silverlight uygulaması akışları.  
  
 Bu tür uygulamalar WCF varlığı önce olası oluşturulurken, WCF uç noktaları geliştirme zamankinden daha kolay hale getirir. Özet olarak, WCF Web Hizmetleri ve Web hizmeti istemcileri oluşturma için yönetilebilir bir yaklaşım sunmak üzere tasarlanmıştır.  
  
## <a name="features-of-wcf"></a>WCF özellikleri  
 WCF aşağıdaki özellik kümesini içerir. Daha fazla bilgi için bkz: [WCF özellik ayrıntıları](../../../docs/framework/wcf/feature-details/index.md).  
  
-   **Hizmet yönlendirmesi**  
  
     WS standartlar kullanarak bir sonucu olduğundan WCF oluşturmanıza olanak sağlayan *yönelik hizmet* uygulamalar. Hizmet odaklı mimari (SOA) veri göndermek ve almak için Web Hizmetleri bağımlılık ' dir. Hizmetler, sabit bir uygulamadan diğerine kodlanmış olan genel avantajı gevşek bağlanmış yerine sahiptir. Birbirine sıkı şekilde bağlı bir ilişki temel sözleşmeleri karşılandığından sürece herhangi bir platformda oluşturulan herhangi bir istemci herhangi bir hizmetin bağlanabildiğinizi anlamına gelir.  
  
-   **Birlikte çalışabilirlik**  
  
     WCF Web hizmeti birlikte çalışabilirlik için modern endüstri standartları uygular. Desteklenen standartları hakkında daha fazla bilgi için bkz: [birlikte çalışabilirlik ve tümleştirme](../../../docs/framework/wcf/feature-details/interoperability-and-integration.md).  
  
-   **Birden çok ileti desenleri**  
  
     İletiler birkaç desenleri birinde değiştirilir. En yaygın düzeni, burada bir uç nokta verileri ikinci uç noktasından ister istek/yanıt Düzen yöneliktir. İkinci uç nokta yanıtlar. Tek bir uç nokta herhangi bir yanıt beklentisi olmadan bir ileti gönderir tek yönlü bir ileti gibi diğer düzenleri vardır. Daha karmaşık bir desen burada iki uç nokta bağlantı kurmak ve veri geri ve ileri bir anlık ileti programı benzer göndermek çift yönlü değişim deseni ' dir. WCF kullanarak desenleri farklı ileti exchange uygulama hakkında daha fazla bilgi için bkz: [sözleşmeleri](../../../docs/framework/wcf/feature-details/contracts.md).  
  
-   **Hizmet meta verileri**  
  
     WCF WSDL, XML şeması ve WS-Policy gibi endüstri standartları belirtilen biçimlerini kullanarak hizmeti meta veri yayımlama destekler. Bu meta veriler otomatik olarak oluşturmak ve WCF hizmetlerine erişmek için istemcileri yapılandırmak için kullanılabilir. Meta veriler, HTTP ve HTTPS yayımlanabilir veya Web hizmeti meta veri değişimi standart kullanma. Daha fazla bilgi için bkz: [meta verileri](../../../docs/framework/wcf/feature-details/metadata.md).  
  
-   **Veri Anlaşmaları**  
  
     WCF kullanılarak oluşturulduğundan [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], ayrıca kod kolay uygulamak istediğiniz sözleşmeleri sağlama yöntemleri içerir. Evrensel türdeki sözleşmelerin veri sözleşmesi biridir. Visual C# veya Visual Basic kullanarak hizmetinizi kod, esas olarak, verileri işlemek için en kolay yolu veri varlığa ait özelliklere sahip bir veri varlığı temsil eden sınıfları oluşturarak aynıdır. WCF Bu kolay şekilde verilerle çalışmak için kapsamlı bir sistem içerir. Verilerini temsil eden sınıfları oluşturduktan sonra hizmetiniz tasarladığınız veri türleriyle uyumlu istemcilerin meta verileri otomatik olarak oluşturur. Daha fazla bilgi için bkz: [kullanarak veri sözleşmeleri](../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
  
-   **Güvenlik**  
  
     Gizliliğinizi korumak için iletileri şifrelenebilir ve iletileri almasına izin verilmeden önce kimlik doğrulaması yapmalarına gerek duyabilirsiniz. Güvenlik, SSL veya WS-SecureConversation gibi bilinen standartları kullanarak uygulanabilir. Daha fazla bilgi için bkz: [güvenlik](../../../docs/framework/wcf/feature-details/security.md).  
  
-   **Birden çok aktarımları ve kodlamaları**  
  
     İletiler hiçbirinde birkaç yerleşik aktarım protokolleri ve Kodlamalar gönderilebilir. En sık kullanılan protokol ve kodlama olan metin kodlanmış World Wide Web üzerinde kullanım için Köprü Metni Aktarım Protokolü (HTTP) kullanarak SOAP iletileri göndermek için. Alternatif olarak, WCF TCP üzerinden iletileri göndermenize olanak sağlayan kanallar veya MSMQ adlı. Bu iletiler olarak kodlanmış metin ya da bir en iyi duruma getirilmiş ikili biçimini kullanarak olarak.  İkili veriler MTOM standart verimli şekilde kullanma gönderilebilir. Sağlanan taşımaları veya Kodlamalar hiçbiri gereksinimlerinize uygun değilse, kendi özel oluşturabilirsiniz taşıma veya kodlama. Taşımalar ve WCF tarafından desteklenen Kodlamalar hakkında daha fazla bilgi için bkz: [taşımaları](../../../docs/framework/wcf/feature-details/transports.md).  
  
-   **Güvenilir ve sıraya alınan iletileri**  
  
     WCF WS güvenilir Mesajlaşma uygulanan ve MSMQ kullanarak güvenilir oturumlar kullanarak güvenilir ileti Exchange'i destekler. WCF güvenilir ve sıraya alınan ileti desteği hakkında daha fazla bilgi için bkz: [kuyruklar ve güvenilir oturumlar](../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).  
  
-   **Dayanıklı iletileri**  
  
     Dayanıklı bir ileti hiçbir zaman iletişimde bir bozulma nedeniyle kaybolur biridir. Dayanıklı ileti deseni iletilerinde her zaman bir veritabanına kaydedilir. Bir kesinti oluşursa, veritabanı bağlantısı geri yüklendiğinde ileti değişimi sürdürmeye sağlar. Windows Workflow Foundation (WF) kullanılarak dayanıklı ileti de oluşturabilirsiniz. Daha fazla bilgi için bkz: [iş akışı Hizmetleri](../../../docs/framework/wcf/feature-details/workflow-services.md).  
  
-   **İşlemler**  
  
     WCF da üç işlem modeli birini kullanarak işlemleri destekler: WS-AtomicTtransactions, API'leri <xref:System.Transactions> ad alanı ve Microsoft Dağıtılmış İşlem Düzenleyicisi. İşlem hakkında daha fazla bilgi için WCF desteği bkz [işlemleri](../../../docs/framework/wcf/feature-details/transactions-in-wcf.md).  
  
-   **AJAX ve REST desteği**  
  
     REST, Gelişmekte olan bir Web 2.0 teknolojisi örneğidir. WCF SAOP zarfına sarmalanmamış "Düz" XML verileri işlemek için yapılandırılabilir. ATOM (bir popüler RSS standart) ve JavaScript nesne gösterimi (JSON) gibi bile olmayan XML biçimleri gibi belirli XML Biçimleri desteklemek için WCF da genişletilebilir.  
  
-   **Genişletilebilirlik**  
  
     WCF mimarisinin genişletilebilirlik noktaları sayısına sahip. Ek özelliği gerekliyse, bir hizmet davranışını özelleştirmenizi giriş noktası sayısını vardır. Noktaları kullanılabilir genişletilebilirlik hakkında daha fazla bilgi için bkz: [genişletme WCF](../../../docs/framework/wcf/extending/index.md).  
  
## <a name="wcf-integration-with-other-microsoft-technologies"></a>Diğer Microsoft teknolojileri ile WCF tümleştirme  
 WCF esnek bir platformdur. Bu aşırı esneklik nedeniyle WCF ayrıca diğer Microsoft ürünleri birkaç kullanılır. Ayrıca bu ürünlerden birini kullanıyorsanız WCF temelleri anlayarak hemen bir avantajı vardır.  
  
 WCF ile eşleştirmeye ilk teknoloji Windows Workflow Foundation (WF) oluştu. İş akışları basitleştirmek "etkinlikler" uygulama geliştirme iş akışı kapsülleyerek adımları Windows Workflow Foundation'ın ilk sürümünde, bir geliştirici iş akışı için bir ana bilgisayar oluşturması gerekiyordu. Windows Workflow Foundation sonraki sürümü WCF ile tümleşik. Bir WCF Hizmeti kolayca barındırılması herhangi bir iş akışının izin; WF/WCF proje türü otomatik olarak seçerek bunu yapabilirsiniz içinde [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].  
  
 Microsoft BizTalk Server R2 WCF iletişimi teknolojisinin da kullanır. BizTalk almak ve veri standartlaştırılmış bir biçimden diğerine dönüştürme için tasarlanmıştır. İleti Merkezi ileti kutusu için ileti katı bir eşleme kullanılarak dönüştürülebilir veya iş akışı altyapısının gibi BizTalk özellikleri birini kullanarak teslim edilmelidir. BizTalk artık ileti kutusu iletileri sunmak için WCF iş kolu (LOB) Bağdaştırıcısı'nı kullanabilirsiniz.  
  
 Microsoft Silverlight, geliştiricilerin (örneğin, video akış) medya yoğunluklu Web siteleri oluşturmalarına izin birlikte çalışabilir, zengin Web uygulamaları oluşturmak için kullanılan bir platformdur. Sürüm 2'den başlayarak, Silverlight WCF WCF uç noktaları için Silverlight uygulamalarını bağlamak için iletişim teknolojisi olarak birleştirilmiş.  
  
 [!INCLUDE[dublin](../../../includes/dublin-md.md)] Uygulama sunucusu iletişim için WCF kullanan uygulamaları dağıtma ve yönetme için özel olarak oluşturulur. [!INCLUDE[dublin2](../../../includes/dublin2-md.md)] WCF özellikli uygulamalar için özellikle tasarlanmış zengin araçları ve yapılandırma seçenekleri içerir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel>  
 [Temel Windows Communication Foundation Kavramları](../../../docs/framework/wcf/fundamental-concepts.md)  
 [Windows Communication Foundation Mimarisi](../../../docs/framework/wcf/architecture.md)  
 [Yönergeler ve En İyi Yöntemler](../../../docs/framework/wcf/guidelines-and-best-practices.md)  
 [Başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md)  
 [Belgeler için Kılavuz](../../../docs/framework/wcf/guide-to-the-documentation.md)  
 [Temel WCF Programlama](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Windows Communication Foundation Örnekleri](http://msdn.microsoft.com/library/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)
