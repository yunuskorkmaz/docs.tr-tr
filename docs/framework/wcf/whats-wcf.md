---
title: Windows Communication Foundation nedir?
description: Hizmet odaklı uygulamalar oluşturmaya yönelik bir çerçeve olan Windows Communication Foundation hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], technology overview
- technology overview [WCF]
- WCF [WCF], technology overview
ms.assetid: 40e1009d-ef15-450b-9848-62eabe5e5738
ms.openlocfilehash: 898211ec4504225413769f2f0dbf2f2c70110c14
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556069"
---
# <a name="what-is-windows-communication-foundation"></a>Windows Communication Foundation nedir?
Windows Communication Foundation (WCF), hizmet yönelimli uygulamalar oluşturmaya yönelik bir çerçevedir. WCF kullanarak, verileri bir hizmet uç noktasından diğerine zaman uyumsuz iletiler olarak gönderebilirsiniz. Hizmet uç noktası, IIS tarafından barındırılan bir sürekli kullanılabilir hizmetin parçası olabilir veya bir uygulamada barındırılan bir hizmet olabilir. Uç nokta, hizmet uç noktasından veri isteyen bir hizmetin istemcisi olabilir. İletiler, tek bir karakter veya bir kelime olarak bir XML olarak gönderilebilir ya da ikili veri akışı gibi karmaşık olabilir. Birkaç örnek senaryo şunlardır:

- İş işlemlerini işlemek için güvenli bir hizmet.

- Trafik raporu ya da başka bir izleme hizmeti gibi geçerli verileri başkalarına sağlayan bir hizmet.

- İki kişinin gerçek zamanlı olarak iletişim kurmasına veya veri alışverişi yapmasına olanak tanıyan bir sohbet hizmeti.

- Veri için bir veya daha fazla hizmeti yoklayan ve mantıksal bir sunuda sunan bir pano uygulaması.

- WCF hizmeti olarak Windows Workflow Foundation kullanılarak uygulanan bir iş akışını ortaya çıkarma.

- En son veri akışları için bir hizmeti yoklamaya yönelik bir Silverlight uygulaması.

Bu tür uygulamalar WCF 'nin mevcut olmasından önce mümkün olsa da WCF, uç noktaların geliştirilmesini her zamankinden daha kolay hale getirir. Özet olarak, WCF, Web Hizmetleri ve Web hizmeti istemcileri oluşturmaya yönelik yönetilebilir bir yaklaşım sunmak üzere tasarlanmıştır.

## <a name="features-of-wcf"></a>WCF özellikleri

WCF aşağıdaki özellik kümesini içerir. Daha fazla bilgi için bkz. [WCF özellik ayrıntıları](./feature-details/index.md).

- **Hizmet yönü**

     WS standartları kullanmanın bir sonucu olarak WCF, *hizmet yönelimli* uygulamalar oluşturmanıza olanak sağlar. Hizmet odaklı mimari (SOA), Web hizmetlerine veri gönderme ve alma konusunda rahatlıdır. Hizmetler, bir uygulamadan diğerine sabit kodlanmış olmak yerine gevşek olarak bağlanmış olmasının genel avantajına sahiptir. Gevşek olarak bağlanmış bir ilişki, herhangi bir platformda oluşturulan herhangi bir istemcinin, gerekli sözleşmelerin karşılandığı sürece herhangi bir hizmete bağlanabileceği anlamına gelir.

- **Birlikte çalışabilirlik**

     WCF, Web hizmeti birlikte çalışabilirliği için modern endüstri standartları uygular. Desteklenen standartlar hakkında daha fazla bilgi için bkz. [birlikte çalışabilirlik ve tümleştirme](./feature-details/interoperability-and-integration.md).

- **Birden çok Ileti deseni**

     İletiler birkaç desenden birinde değiştirilir. En yaygın model, bir uç noktanın ikinci bir uç noktadan veri istediği istek/yanıt modelidir. İkinci uç nokta yanıt verir. Tek bir uç noktanın bir yanıtın beklentisi olmadan ileti gönderdiği tek yönlü ileti gibi başka desenler de vardır. Daha karmaşık bir model, iki uç noktanın bir bağlantı kurmasını ve verileri bir anlık ileti programına benzer bir şekilde geri göndermesini ve geri göndermesini sağlar. WCF kullanarak farklı ileti değişimi düzenlerini uygulama hakkında daha fazla bilgi için bkz. [sözleşmeleri](./feature-details/contracts.md).

- **Hizmet meta verileri**

     WCF, WSDL, XML Schema ve WS-Policy gibi sektör standartlarında belirtilen biçimleri kullanarak hizmet meta verilerini yayımlamayı destekler. Bu meta veriler, WCF hizmetlerine erişim için istemcileri otomatik olarak oluşturmak ve yapılandırmak üzere kullanılabilir. Meta veriler HTTP ve HTTPS üzerinden yayımlanabilir veya Web hizmeti meta veri değişimi standardı kullanılarak yapılandırılabilir. Daha fazla bilgi için bkz. [meta veriler](./feature-details/metadata.md).

- **Veri Sözleşmeleri**

     WCF .NET Framework kullanılarak oluşturulduğundan, zorlamak istediğiniz sözleşmeleri sağlamaya yönelik kod kullanımı kolay yöntemler de içerir. Evrensel türdeki sözleşmeler, veri sözleşmelerinden biridir. Temelde, Visual C# veya Visual Basic kullanarak hizmetinizi kodlarınızda, verileri işlemenin en kolay yolu, veri varlığına ait özelliklerle bir veri varlığını temsil eden sınıflar oluşturmaktır. WCF, verilerle bu kolay şekilde çalışmaya yönelik kapsamlı bir sistem içerir. Verileri temsil eden sınıfları oluşturduktan sonra hizmetiniz, tasarlanan veri türleriyle uyumlu olmasını sağlayan meta verileri otomatik olarak oluşturur. Daha fazla bilgi için bkz. [Veri Sözleşmelerini Kullanma](feature-details/using-data-contracts.md).

- **Güvenlik**

     Gizli iletiler, gizliliği korumak için şifrelenebilir ve kullanıcıların ileti almasına izin verilmeden önce kimlik doğrulamasından geçmesini zorunlu kılabilirsiniz. Güvenlik, SSL veya WS-SecureConversation gibi iyi bilinen standartlar kullanılarak uygulanabilir. Daha fazla bilgi için bkz. [güvenlik](./feature-details/security.md).

- **Çoklu aktarımlar ve kodlamalar**

     İletiler, çeşitli yerleşik taşıma protokollerinden ve kodlamalarda gönderilebilir. En yaygın protokol ve kodlama, World Wide Web kullanım için Köprü Metni Aktarım Protokolü (HTTP) kullanarak metin kodlu SOAP iletileri göndermektir. Alternatif olarak, WCF TCP, adlandırılmış kanallar veya MSMQ üzerinden iletiler göndermenizi sağlar. Bu iletiler metin olarak kodlanabilir veya iyileştirilmiş bir ikili biçimi kullanıyor olabilir.  İkili veriler, MTOM standardı kullanılarak verimli bir şekilde gönderilebilir. Belirtilen aktarımların veya kodlamaların hiçbiri ihtiyaçlarınıza uygun değilse kendi özel bir aktarım veya kodlama oluşturabilirsiniz. WCF tarafından desteklenen aktarımlar ve kodlamalar hakkında daha fazla bilgi için bkz. [taşımalar](./feature-details/transports.md).

- **Güvenilir ve kuyruğa alınan Iletiler**

     WCF, WS-güvenilir mesajlaşma ve MSMQ kullanılarak uygulanan güvenilir oturumları kullanarak güvenilir ileti değişimini destekler. WCF 'de güvenilir ve kuyruğa alınmış mesajlaşma desteği hakkında daha fazla bilgi için bkz. [Kuyruklar ve güvenilir oturumlar](./feature-details/queues-and-reliable-sessions.md).

- **Dayanıklı Iletiler**

     Dayanıklı bir ileti, iletişimdeki kesintiden dolayı hiçbir şekilde kaybedilmez. Dayanıklı bir ileti düzenindeki iletiler her zaman bir veritabanına kaydedilir. Bir kesinti oluşursa, veritabanı bağlantı geri yüklendiğinde ileti değişimini sürdürmeniz için izin verir. Windows Workflow Foundation (WF) kullanarak da dayanıklı bir ileti oluşturabilirsiniz. Daha fazla bilgi için bkz. [Workflow Services](./feature-details/workflow-services.md).

- **İşlemler**

     WCF Ayrıca üç işlem modelinden birini kullanarak işlemleri destekler: WS-AtomicTransactions, <xref:System.Transactions> ad alanındaki API 'ler ve Microsoft Dağıtılmış işlem Düzenleyicisi. WCF 'de işlem desteği hakkında daha fazla bilgi için bkz. [işlemler](./feature-details/transactions-in-wcf.md).

- **AJAX ve REST desteği**

     REST, gelişen Web 2,0 teknolojisine bir örnektir. WCF, bir SOAP zarfında sarmalanmamış "düz" XML verilerini işleyecek şekilde yapılandırılabilir. WCF Ayrıca, ATOM (popüler bir RSS standardı) gibi belirli XML biçimlerini ve hatta JavaScript Nesne Gösterimi (JSON) gibi XML olmayan biçimleri desteklemek için de genişletilebilir.

- **Genişletilebilirlik**

     WCF mimarisi birçok genişletilebilirlik noktasına sahiptir. Ek yetenek gerekliyse, bir hizmetin davranışını özelleştirmenizi sağlayan çeşitli giriş noktaları vardır. Kullanılabilir genişletilebilirlik noktaları hakkında daha fazla bilgi için bkz. [WCF genişletme](./extending/index.md).

## <a name="wcf-integration-with-other-microsoft-technologies"></a>Diğer Microsoft teknolojileriyle WCF tümleştirmesi

WCF, esnek bir platformdur. Bu aşırı esneklik nedeniyle, WCF diğer birçok Microsoft ürününde de kullanılır. WCF temel bilgilerini öğrenerek, bu ürünlerden herhangi birini de kullanıyorsanız, hemen avantajınız vardır.

WCF ile eşleştirmeye yönelik ilk teknoloji Windows Workflow Foundation (WF) idi. İş akışları, iş akışındaki adımları "Etkinlikler" olarak kapsülleyerek uygulama geliştirmeyi basitleştirir. Windows Workflow Foundation ilk sürümünde, bir geliştiricinin iş akışı için bir konak oluşturması gerekiyordu. Windows Workflow Foundation sonraki sürümü WCF ile tümleştirildi. Bu, herhangi bir iş akışının bir WCF hizmetinde kolayca barındırılmasına izin verilir. Bunu, Visual Studio 2012 veya sonraki sürümlerde WF/WCF proje türünü otomatik olarak seçerek yapabilirsiniz.

Microsoft BizTalk Server R2 Ayrıca WCF 'yi bir iletişim teknolojisi olarak kullanır. BizTalk, verileri standartlaştırılmış bir biçimden diğerine alıp dönüştürmek üzere tasarlanmıştır. İletiler, iletinin katı eşleme kullanılarak veya iş akışı altyapısı gibi BizTalk özelliklerinden biri kullanılarak dönüştürülebileceği merkezi ileti kutusuna teslim alınmalıdır. BizTalk, ileti kutusuna ileti teslim etmek için artık WCF Iş kolu (LOB) bağdaştırıcı kullanabilir.

Microsoft Silverlight, geliştiricilerin medya yoğun Web siteleri (örneğin, akış videosu) oluşturmalarına olanak tanıyan, birlikte çalışabilen zengin Web uygulamaları oluşturmaya yönelik bir platformdur. Sürüm 2 ' den başlayarak, Silverlight, Silverlight uygulamalarını WCF uç noktalarına bağlamaya yönelik bir iletişim teknolojisi olarak WCF 'yi içerir.

Windows Server AppFabric uygulama sunucusunun barındırma özellikleri, iletişim için WCF kullanan uygulamaları dağıtmak ve yönetmek için özel olarak tasarlanmıştır. Barındırma özellikleri, WCF özellikli uygulamalar için özel olarak tasarlanmış zengin araç ve yapılandırma seçeneklerini içerir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel>
- [Temel Windows Communication Foundation Kavramları](fundamental-concepts.md)
- [Windows Communication Foundation Mimarisi](architecture.md)
- [Yönergeler ve En İyi Yöntemler](guidelines-and-best-practices.md)
- [Başlangıç Öğreticisi](getting-started-tutorial.md)
- [Belgeler için Kılavuz](guide-to-the-documentation.md)
- [Temel WCF Programlama](basic-wcf-programming.md)
- [Windows Communication Foundation Örnekleri](/previous-versions/dotnet/netframework-3.5/ms751514(v=vs.90))
