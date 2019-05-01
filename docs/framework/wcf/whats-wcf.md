---
title: Windows Communication Foundation nedir?
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], technology overview
- technology overview [WCF]
- WCF [WCF], technology overview
ms.assetid: 40e1009d-ef15-450b-9848-62eabe5e5738
ms.openlocfilehash: a2d0ef1e70c88133d5f9c3d2ffe8dafa4983cfd9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904558"
---
# <a name="what-is-windows-communication-foundation"></a>Windows Communication Foundation nedir?
Windows Communication Foundation (WCF) hizmet odaklı uygulamalar oluşturmaya yönelik bir çerçevedir. WCF kullanarak, verileri zaman uyumsuz ileti olarak bir hizmetin uç noktasından diğerine gönderebilirsiniz. Hizmet uç noktası, IIS tarafından barındırılan sürekli olarak kullanılabilir bir hizmetin parçası veya barındırılan bir uygulamada bir hizmet olabilir. Bir uç nokta, bir istemci bir hizmet uç noktasından verileri isteyen bir hizmet olabilir. İletileri bir tek karakter ya da XML olarak gönderilen word kadar basit veya bir ikili veri akışı gibi karmaşık olabilir. Bazı örnek senaryolar şunlardır:

- İş işlemleri için güvenli bir hizmet.

- Trafik rapor ya da diğer izleme hizmeti gibi diğer kullanıcılarla, geçerli veri sağlayan bir hizmettir.

- İletişim veya gerçek zamanlı veri değişimi iki kişinin sağlayan bir sohbet hizmeti.

- Veriler için bir veya daha fazla hizmet yoklar ve mantıksal sunuda sunan bir Pano uygulaması.

- Bir WCF hizmeti olarak Windows Workflow Foundation kullanılarak uygulanan bir iş akışı gösterme.

- Bir Silverlight uygulamasını bir hizmet için en yeni verileri yoklamak üzere akışları.

Söz konusu uygulamalar WCF varlığını önce olası oluşturulurken, WCF uç noktaları geliştirilmesini her zamankinden daha kolay hale getirir. Özet olarak, WCF Web hizmetlerini ve Web hizmeti istemcileriyle oluşturma yönetilebilir bir yaklaşım sunmak üzere tasarlanmıştır.

## <a name="features-of-wcf"></a>WCF özellikleri

WCF aşağıdaki özellikleri içerir. Daha fazla bilgi için [WCF özellik ayrıntıları](../../../docs/framework/wcf/feature-details/index.md).

- **Hizmet yönlendirmesi**

     WS standartları kullanarak, bir sonucu olan WCF oluşturmanıza olanak sağlayan *hizmet odaklı* uygulamalar. Hizmet odaklı mimari (SOA) veri göndermek ve almak için Web Hizmetleri güvenme ' dir. Hizmetleri olma genel avantajı zamanı gevşek bağlanmış yerine bir uygulamadan diğerine kodlanmış vardır. Zamanı gevşek bağlanmış bir ilişki temel anlaşmalar karşılandığından sürece herhangi bir platform üzerinde oluşturulan herhangi bir istemci herhangi bir hizmete bağlanabilir anlamına gelir.

- **Birlikte çalışabilirlik**

     WCF Web hizmeti birlikte çalışabilirlik modern endüstri standartlarını uygular. Desteklenen standartları hakkında daha fazla bilgi için bkz. [birlikte çalışabilirlik ve tümleştirme](../../../docs/framework/wcf/feature-details/interoperability-and-integration.md).

- **Birden çok ileti desenleri**

     İletiler çeşitli desenlerden birini değiştirilir. Burada bir uç nokta ikinci bir uç noktasından veri istekleri istek/yanıt deseni en yaygın desen var. İkinci uç nokta yanıtlar. Bir tek yönlü mesaj, tek bir uç nokta herhangi bir yanıt beklentisi olmadan bir ileti gönderir gibi diğer düzenleri vardır. Burada iki uç nokta bağlantı kurmak ve verileri geri ve ileri bir anlık Mesajlaşma programına benzer göndermesini çift yönlü değişim deseni buna daha karmaşık bir desendir. WCF kullanarak desenlerini nasıl farklı ileti değişimi uygulanacağı hakkında daha fazla bilgi için bkz [sözleşmeleri](../../../docs/framework/wcf/feature-details/contracts.md).

- **Hizmet meta verileri**

     WCF WSDL, XML şema ve WS-Policy gibi endüstri standartlarından belirtilen biçimi kullanarak Yayımlama hizmeti meta verileri destekler. Bu meta veriler otomatik olarak oluşturmak ve WCF hizmetlerine erişmek için istemcileri yapılandırmak için kullanılabilir. Meta verileri, HTTP ve HTTPS üzerinden yayımlanabilir veya Web hizmeti meta veri değişimi standardını kullanarak. Daha fazla bilgi için [meta verileri](../../../docs/framework/wcf/feature-details/metadata.md).

- **Veri Anlaşmaları**

     WCF kullanarak inşa edildiğinden [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], ayrıca kod dostu uygulamak istediğiniz sözleşmeleri sağlama yöntemleri içerir. Sözleşmeler Evrensel tür veri anlaşması biridir. Visual C# veya Visual Basic kullanarak hizmetinizin kod gibi esas olarak, verileri işlemek için en kolay yolu, veri varlığına ait özelliklere sahip bir veri varlığı temsil eden sınıflar oluşturmaktır. Bu kolay bir şekilde verilerle çalışmaya yönelik kapsamlı bir sistem WCF içerir. Verileri temsil eden sınıfları oluşturduktan sonra hizmetinizin tasarladığınız veri türleriyle uyumlu istemcilerin meta verileri otomatik olarak oluşturur. Daha fazla bilgi için [kullanarak veri sözleşmeleri](../../../docs/framework/wcf/feature-details/using-data-contracts.md)

- **Güvenlik**

     Gizliliğinizi korumak için iletileri şifrelenebilir ve kullanıcıların iletileri almasına izin verilmeden önce kimlik doğrulaması gerektirebilir. Güvenlik, SSL veya WS-SecureConversation gibi iyi bilinen standartları kullanarak uygulanabilir. Daha fazla bilgi için [güvenlik](../../../docs/framework/wcf/feature-details/security.md).

- **Birden çok aktarımları ve kodlamaları**

     İletileri herhangi birkaç yerleşik aktarım protokolünü ve kodlamaları gönderilebilir. En sık kullanılan protokol ve kodlama olan metin kodlanmış SOAP iletilerini World Wide Web üzerinde kullanım için Köprü Metni Aktarım Protokolü (HTTP) kullanarak göndermek için. Alternatif olarak, WCF, TCP üzerinden iletileri göndermenizi sağlar kanallar veya MSMQ adlı. Bu iletiler kodlanmış metin ya da en iyi duruma getirilmiş bir ikili biçimi kullanarak.  İkili verileri verimli bir şekilde MTOM standardını kullanarak gönderilebilir. Sağlanan taşımalar veya Kodlamalar hiçbiri gereksinimlerinize uygun değilse kendi özel oluşturabilirsiniz taşıma veya kodlama. Aktarım ve WCF tarafından desteklenen Kodlamalar hakkında daha fazla bilgi için bkz. [taşımalar](../../../docs/framework/wcf/feature-details/transports.md).

- **Güvenilir ve kuyruğa alınmış iletileri**

     WCF WS-Reliable Mesajlaşma uygulanan ve MSMQ kullanarak güvenilir oturumlar kullanan güvenilir ileti alışverişi destekler. Wcf'de güvenilir ve kuyruğa alınan Mesajlaşma desteği hakkında daha fazla bilgi için bkz. [kuyruklar ve güvenilir oturumlar](../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).

- **Dayanıklı ileti**

     Dayanıklı ileti asla iletişim kesinti nedeniyle kayıp biridir. Dayanıklı ileti deseni iletilerin her zaman bir veritabanına kaydedilir. Bir kesinti oluşursa, veritabanı bağlantı geri geldiğinde, iletiyi exchange sürdürmek sağlar. Ayrıca, Windows Workflow Foundation (WF) kullanarak dayanıklı ileti oluşturabilirsiniz. Daha fazla bilgi için [iş akışı Hizmetleri](../../../docs/framework/wcf/feature-details/workflow-services.md).

- **İşlemler**

     WCF işlem üç işlem modeli kullanarak da destekler: WS-AtomicTtransactions, API'leri <xref:System.Transactions> ad ve Microsoft Dağıtılmış İşlem Düzenleyicisi. Wcf'de destek işlem hakkında daha fazla bilgi için bkz [işlemleri](../../../docs/framework/wcf/feature-details/transactions-in-wcf.md).

- **AJAX ve REST desteği**

     REST, gelişen bir Web 2.0 teknolojisini örneğidir. WCF bir SOAP Zarfı içinde sarmalanmamış "Düz" XML verileri işlemek için yapılandırılabilir. WCF ayrıca ATOM (bir popüler RSS standart) ve JavaScript nesne gösterimi (JSON) gibi bile XML olmayan biçimleri gibi belirli XML Biçimleri destekleyecek şekilde genişletilebilir.

- **Genişletilebilirlik**

     WCF mimarisinin bir dizi genişletilebilirlik noktaları vardır. Fazladan yetenek gerekiyorsa, bir hizmet davranışını özelleştirmenizi giriş noktaları sayısı vardır. Kullanılabilir genişletilebilirlik hakkında daha fazla bilgi için bkz: noktaları [genişletme WCF](../../../docs/framework/wcf/extending/index.md).

## <a name="wcf-integration-with-other-microsoft-technologies"></a>Diğer Microsoft teknolojileri ile WCF tümleştirmesi

WCF esnek bir platformdur. Bu aşırı esnekliği sunmamız nedeniyle, WCF, diğer Microsoft ürünlerinde birkaç de kullanılır. WCF ile ilgili temel bilgileri anlayarak, ayrıca bu ürünlerden birini kullanırsanız hemen bir avantajı da vardır.

WCF ile kullanmak üzere ilk teknoloji Windows Workflow Foundation (WF) oluştu. İş akışları uygulama geliştirmeyi kapsayan iş akışı adımları olarak "etkinlikler" basitleştirin Windows Workflow Foundation'ın ilk sürümünde, iş akışı için bir ana bilgisayar oluşturmak bir geliştirici vardı. WCF ile tümleşik Windows Workflow Foundation'ın sonraki sürümü. Bir WCF Hizmeti kolayca barındırılması herhangi bir iş akışının izin verilir. Visual Studio 2012 veya sonraki bir sürümde WF/WCF proje türü otomatik olarak seçerek bunu yapabilirsiniz.

Microsoft BizTalk Server R2, ayrıca WCF iletişim teknolojisi olarak kullanır. BizTalk alma ve standartlaştırılmış bir biçimden diğerine dönüştürme tasarlanmıştır. İleti Merkezi ileti kutusu için ileti katı bir eşleme kullanılarak dönüştürülüp veya kendi iş akışı altyapısı gibi BizTalk özellikleri birini kullanarak teslim edilmelidir. BizTalk artık ileti kutusuna iletileri ulaştırmak üzere WCF satır iş kolu (LOB) Bağdaştırıcısı'nı kullanabilirsiniz.

Microsoft Silverlight geliştiriciler (örneğin, video akışı) medya yoğunluklu Web siteleri oluşturmasına imkan tanıyan birlikte çalışabilir ve zengin Web uygulamaları oluşturmaya yönelik bir platformdur. Sürüm 2 ile başlayarak, Silverlight, WCF bitiş noktalarını Silverlight uygulamalarını bağlamak için iletişim teknolojisi olarak WCF yaptıysa.

[!INCLUDE[dublin](../../../includes/dublin-md.md)] Uygulama sunucusu iletişimi için WCF kullanan uygulamaları dağıtma ve yönetme için özel olarak oluşturulmuştur. [!INCLUDE[dublin2](../../../includes/dublin2-md.md)] WCF özellikli uygulamalar için özel olarak tasarlanmış zengin araç ve yapılandırma seçenekleri içerir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel>
- [Temel Windows Communication Foundation Kavramları](../../../docs/framework/wcf/fundamental-concepts.md)
- [Windows Communication Foundation Mimarisi](../../../docs/framework/wcf/architecture.md)
- [Yönergeler ve En İyi Yöntemler](../../../docs/framework/wcf/guidelines-and-best-practices.md)
- [Başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md)
- [Belgeler için Kılavuz](../../../docs/framework/wcf/guide-to-the-documentation.md)
- [Temel WCF Programlama](../../../docs/framework/wcf/basic-wcf-programming.md)
- [Windows Communication Foundation Örnekleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751514%28v=vs.90%29)
