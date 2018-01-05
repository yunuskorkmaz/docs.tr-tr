---
title: Windows Communication Foundation nedir?
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation [WCF], technology overview
- technology overview [WCF]
- WCF [WCF], technology overview
ms.assetid: 40e1009d-ef15-450b-9848-62eabe5e5738
caps.latest.revision: "51"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f5301bf3a2fed35dbdd0046e01eb2acb9083a290
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="what-is-windows-communication-foundation"></a>Windows Communication Foundation nedir?
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]Hizmet odaklı uygulamalar oluşturmaya yönelik bir çerçevedir. Kullanarak [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], verileri zaman uyumsuz ileti bir hizmet uç noktasından diğerine gönderebilirsiniz. Hizmet uç noktası, IIS tarafından barındırılan sürekli olarak kullanılabilir bir hizmetin parçası veya bir uygulamada barındırılan bir hizmete olabilir. Bir uç nokta veri Hizmeti uç noktasından ister bir hizmetin istemci olabilir. İletileri tek karakter veya XML olarak gönderilen sözcük kadar basit ya da bir ikili veri akışı kadar karmaşık olabilir. Bazı örnek senaryolar şunlardır:  
  
-   İş işlemleri için güvenli bir hizmet.  
  
-   Bir trafik rapor veya diğer izleme hizmeti gibi başkalarına, geçerli veri sağlayan bir hizmet.  
  
-   İletişim veya gerçek zamanlı veri değişimi iki kişinin sağlayan bir sohbet hizmeti.  
  
-   Bir veya daha fazla yoklar bir Pano uygulaması için Veri Hizmetleri ve bir mantıksal sunuya sunar.  
  
-   WCF hizmet olarak Windows Workflow Foundation kullanılarak uygulanan bir iş akışı gösterme.  
  
-   Bir hizmet için en yeni verileri yoklamak için Silverlight uygulaması akışları.  
  
 Bu tür uygulamalar varlığını önce olası oluşturulurken [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] uç noktaları geliştirme zamankinden daha kolay hale getirir. Özet olarak, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Web Hizmetleri ve Web hizmeti istemcileri oluşturma için yönetilebilir bir yaklaşım sunmak üzere tasarlanmıştır.  
  
## <a name="features-of-wcf"></a>WCF özellikleri  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]Aşağıdaki özellikler kümesi içerir. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][WCF özellik ayrıntıları](../../../docs/framework/wcf/feature-details/index.md).  
  
-   **Hizmet yönlendirmesi**  
  
     WS standartlar kullanarak bir sonucu olduğundan [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] oluşturmanızı sağlayan *yönelik hizmet* uygulamalar. Hizmet odaklı mimari (SOA) veri göndermek ve almak için Web Hizmetleri bağımlılık ' dir. Hizmetler, sabit bir uygulamadan diğerine kodlanmış olan genel avantajı gevşek bağlanmış yerine sahiptir. Birbirine sıkı şekilde bağlı bir ilişki temel sözleşmeleri karşılandığından sürece herhangi bir platformda oluşturulan herhangi bir istemci herhangi bir hizmetin bağlanabildiğinizi anlamına gelir.  
  
-   **Birlikte çalışabilirlik**  
  
     [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]Web hizmeti birlikte çalışabilirlik için modern endüstri standartları uygular. [!INCLUDE[crabout](../../../includes/crabout-md.md)]desteklenen standartlar bkz [birlikte çalışabilirlik ve tümleştirme](../../../docs/framework/wcf/feature-details/interoperability-and-integration.md).  
  
-   **Birden çok ileti desenleri**  
  
     İletiler birkaç desenleri birinde değiştirilir. En yaygın düzeni, burada bir uç nokta verileri ikinci uç noktasından ister istek/yanıt Düzen yöneliktir. İkinci uç nokta yanıtlar. Tek bir uç nokta herhangi bir yanıt beklentisi olmadan bir ileti gönderir tek yönlü bir ileti gibi diğer düzenleri vardır. Daha karmaşık bir desen burada iki uç nokta bağlantı kurmak ve veri geri ve ileri bir anlık ileti programı benzer göndermek çift yönlü değişim deseni ' dir. [!INCLUDE[crabout](../../../includes/crabout-md.md)]farklı ileti exchange uygulama düzenleri kullanarak [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] bkz [sözleşmeleri](../../../docs/framework/wcf/feature-details/contracts.md).  
  
-   **Hizmet meta verileri**  
  
     [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]Hizmet meta verilerini WSDL, XML şeması ve WS-Policy gibi endüstri standartları belirtilen biçimlerini kullanarak yayımlamayı destekler. Bu meta veriler otomatik olarak oluşturmak ve erişmek için istemcileri yapılandırmak için kullanılan [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Hizmetleri. Meta veriler, HTTP ve HTTPS yayımlanabilir veya Web hizmeti meta veri değişimi standart kullanma. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Meta verileri](../../../docs/framework/wcf/feature-details/metadata.md).  
  
-   **Veri Anlaşmaları**  
  
     Çünkü [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] kullanılarak oluşturulan [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], ayrıca kod kolay uygulamak istediğiniz sözleşmeleri sağlama yöntemleri içerir. Evrensel türdeki sözleşmelerin veri sözleşmesi biridir. Visual C# veya Visual Basic kullanarak hizmetinizi kod, esas olarak, verileri işlemek için en kolay yolu veri varlığa ait özelliklere sahip bir veri varlığı temsil eden sınıfları oluşturarak aynıdır. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]Bu kolay şekilde verilerle çalışmak için kapsamlı bir sistem içerir. Verilerini temsil eden sınıfları oluşturduktan sonra hizmetiniz tasarladığınız veri türleriyle uyumlu istemcilerin meta verileri otomatik olarak oluşturur. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Veri sözleşmelerini kullanma](../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
  
-   **Güvenlik**  
  
     Gizliliğinizi korumak için iletileri şifrelenebilir ve iletileri almasına izin verilmeden önce kimlik doğrulaması yapmalarına gerek duyabilirsiniz. Güvenlik, SSL veya WS-SecureConversation gibi bilinen standartları kullanarak uygulanabilir. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Güvenlik](../../../docs/framework/wcf/feature-details/security.md).  
  
-   **Birden çok aktarımları ve kodlamaları**  
  
     İletiler hiçbirinde birkaç yerleşik aktarım protokolleri ve Kodlamalar gönderilebilir. En yaygın protokolü ve kodlama kullanarak kodlanmış metin SOAP iletileri göndermesini Köprü Metni Aktarım Protokolü (HTTP) World Wide Web üzerinde kullanılmak üzere etmektir. Alternatif olarak, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] kanallar veya MSMQ adlı TCP üzerinden iletileri göndermenize izin verir. Bu iletiler olarak kodlanmış metin ya da bir en iyi duruma getirilmiş ikili biçimini kullanarak olarak.  İkili veriler MTOM standart verimli şekilde kullanma gönderilebilir. Sağlanan taşımaları veya Kodlamalar hiçbiri gereksinimlerinize uygun değilse, kendi özel oluşturabilirsiniz taşıma veya kodlama. [!INCLUDE[crabout](../../../includes/crabout-md.md)]taşımalar ve tarafından desteklenen Kodlamalar [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] bkz [taşımaları](../../../docs/framework/wcf/feature-details/transports.md).  
  
-   **Güvenilir ve sıraya alınan iletileri**  
  
     [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]WS güvenilir Mesajlaşma uygulanan ve MSMQ kullanarak güvenilir oturumlar kullanarak güvenilir ileti Exchange'i destekler. [!INCLUDE[crabout](../../../includes/crabout-md.md)]güvenilir ve sıraya alınan ileti desteği [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] bkz [kuyruklar ve güvenilir oturumlar](../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).  
  
-   **Dayanıklı iletileri**  
  
     Dayanıklı bir ileti hiçbir zaman iletişimde bir bozulma nedeniyle kaybolur biridir. Dayanıklı ileti deseni iletilerinde her zaman bir veritabanına kaydedilir. Bir kesinti oluşursa, veritabanı bağlantısı geri yüklendiğinde ileti değişimi sürdürmeye sağlar. Dayanıklı bir iletiyi kullanarak da oluşturabilirsiniz [!INCLUDE[wf](../../../includes/wf-md.md)]. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][İş akışı Hizmetleri](../../../docs/framework/wcf/feature-details/workflow-services.md).  
  
-   **İşlemler**  
  
     WCF da üç işlem modeli birini kullanarak işlemleri destekler: WS-AtomicTtransactions, API'leri <xref:System.Transactions> ad alanı ve Microsoft Dağıtılmış İşlem Düzenleyicisi. [!INCLUDE[crabout](../../../includes/crabout-md.md)]işlem desteği, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] bkz [işlemleri](../../../docs/framework/wcf/feature-details/transactions-in-wcf.md).  
  
-   **AJAX ve REST desteği**  
  
     REST, Gelişmekte olan bir Web 2.0 teknolojisi örneğidir. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]bir SOAP Zarfı sarmalanmamış "Düz" XML verileri işlemek için yapılandırılabilir. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]Ayrıca ATOM (bir popüler RSS standart) ve JavaScript nesne gösterimi (JSON) gibi bile olmayan XML biçimleri gibi belirli XML Biçimleri desteklemek için genişletilebilir.  
  
-   **Genişletilebilirlik**  
  
     [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Mimariye sahip genişletilebilirlik noktaları sayısı. Ek özelliği gerekliyse, bir hizmet davranışını özelleştirmenizi giriş noktası sayısını vardır. [!INCLUDE[crabout](../../../includes/crabout-md.md)]kullanılabilir genişletilebilirlik noktaları Bkz [genişletme WCF](../../../docs/framework/wcf/extending/extending-wcf.md).  
  
## <a name="wcf-integration-with-other-microsoft-technologies"></a>Diğer Microsoft teknolojileri ile WCF tümleştirme  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]esnek bir platformdur. Bu aşırı esneklik nedeniyle [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] diğer Microsoft ürünleri birkaç de kullanılır. Temelleri anlama tarafından [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], ayrıca bu ürünlerden birini kullanırsanız hemen bir avantajı vardır.  
  
 Eşleştirmeye ilk teknolojisi [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Windows Workflow Foundation (WF) oluştu. İş akışları basitleştirmek "etkinlikler" uygulama geliştirme iş akışı kapsülleyerek adımları İlk sürümünde [!INCLUDE[wf2](../../../includes/wf2-md.md)], bir geliştirici iş akışı için bir ana bilgisayar oluşturması gerekiyordu. Sonraki sürümü [!INCLUDE[wf2](../../../includes/wf2-md.md)] ile tümleşik [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]. İçinde kolayca barındırılması herhangi bir iş akışının izin verilen bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service; bunu yapabilirsiniz otomatik olarak bir proje türü WF/WCF'i seçerek de [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].  
  
 Microsoft BizTalk Server R2'in de kullanacağını [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] iletişim teknolojisi olarak. BizTalk almak ve veri standartlaştırılmış bir biçimden diğerine dönüştürme için tasarlanmıştır. İleti Merkezi ileti kutusu için ileti katı bir eşleme kullanılarak dönüştürülebilir veya iş akışı altyapısının gibi BizTalk özellikleri birini kullanarak teslim edilmelidir. BizTalk şimdi kullanabileceğiniz [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ileti kutusu iletileri sunmak için iş kolu (LOB) bağdaştırıcısı.  
  
 Microsoft Silverlight, geliştiricilerin (örneğin, video akış) medya yoğunluklu Web siteleri oluşturmalarına izin birlikte çalışabilir, zengin Web uygulamaları oluşturmak için kullanılan bir platformdur. Sürüm 2'den başlayarak, Silverlight dahil [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Silverlight uygulamalarını bağlamak için iletişim teknolojisi olarak [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] uç noktaları.  
  
 [!INCLUDE[dublin](../../../includes/dublin-md.md)] Uygulama sunucusu dağıtma ve kullanan uygulamaları yönetmek için özel olarak oluşturulmuş [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] iletişimi için. [!INCLUDE[dublin2](../../../includes/dublin2-md.md)] İçin özellikle tasarlanmış zengin araçları ve yapılandırma seçeneklerini içeren [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]-etkin olan uygulamalar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel>  
 [Temel Windows Communication Foundation Kavramları](../../../docs/framework/wcf/fundamental-concepts.md)  
 [Windows Communication Foundation Mimarisi](../../../docs/framework/wcf/architecture.md)  
 [Yönergeler ve En İyi Yöntemler](../../../docs/framework/wcf/guidelines-and-best-practices.md)  
 [Başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md)  
 [Belgeler için Kılavuz](../../../docs/framework/wcf/guide-to-the-documentation.md)  
 [Temel WCF Programlama](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Windows Communication Foundation Örnekleri](http://msdn.microsoft.com/en-us/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)
