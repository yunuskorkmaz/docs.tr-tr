---
title: ASP.NET Önbelleğe Alma Tümleştirmesi
ms.date: 03/30/2017
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
ms.openlocfilehash: 23c10e56dba7daec2d1027de92e8252c8fe69055
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716171"
---
# <a name="aspnet-caching-integration"></a>ASP.NET Önbelleğe Alma Tümleştirmesi

Bu örnek, WCF WEB HTTP programlama modeliyle ASP.NET çıktı önbelleğinin nasıl kullanıldığını gösterir. Bu konu, ASP.NET çıktı önbelleği tümleştirme özelliğine odaklanır.

## <a name="demonstrates"></a>Gösterir

ASP.NET çıktı önbelleğiyle tümleştirme

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`

## <a name="discussion"></a>Tartışma

Örnek, Windows Communication Foundation (WCF) hizmeti ile ASP.NET çıktı önbelleği kullanmak için <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> kullanır. <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, hizmet işlemlerine uygulanır ve belirli bir işlemden alınan yanıtlara uygulanması gereken bir yapılandırma dosyasında Önbellek profilinin adını sağlar.

Örnek hizmet projesinin Service.cs dosyasında, hem `GetCustomer` hem de `GetCustomers` işlemler, "CacheFor60Seconds" önbellek profili adını sağlayan <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>ile işaretlenir. Hizmet projesinin Web. config dosyasında, "CacheFor60Seconds" önbellek profili, <`system.web`> <`caching`> öğesi altında sağlanır. Bu önbellek profili için `duration` özniteliğinin değeri "60" olur, bu nedenle bu profille ilişkili yanıtlar 60 saniye için ASP.NET çıktı önbelleğinde önbelleğe alınır. Ayrıca, bu önbellek profili için, `varmByParam` özniteliği "biçim" olarak ayarlanır, böylece `format` sorgu dizesi parametresi için farklı değerlere sahip isteklerin yanıtları ayrı olarak önbelleğe alınır. Son olarak, Önbellek profilinin `varyByHeader` özniteliği "kabul et" olarak ayarlanır; bu nedenle, farklı Accept üst bilgisi değerlerine sahip isteklerin yanıtları ayrı olarak önbelleğe alınır.

Istemci projesindeki Program.cs, bu tür bir istemcinin <xref:System.Net.HttpWebRequest>kullanarak nasıl yazılıp yazıldığının gösterir. Bu, bir WCF hizmetine erişmenin yalnızca bir yoludur. WCF kanal fabrikası ve <xref:System.Net.WebClient>gibi diğer .NET Framework sınıfları kullanılarak hizmete de erişebilirsiniz. SDK 'daki diğer örnekler ( [temel http hizmet](../../../../docs/framework/wcf/samples/basic-http-service.md) örneği gibi), bu SıNıFLARıN bir WCF hizmeti ile iletişim kurmak için nasıl kullanılacağını gösterir.

## <a name="to-run-the-sample"></a>Örnek çalıştırmak için

Örnek üç projeden oluşur:

- **Hizmet**: ASP.NET içinde BARıNDıRıLAN BIR WCF HTTP hizmetini Içeren bir Web uygulaması projesi.

- **İstemci**: hizmete çağrı yapan bir konsol uygulaması projesi.

- **Ortak**: istemci ve hizmet tarafından kullanılan müşteri türünü içeren paylaşılan bir kitaplıktır.

Istemci konsol uygulaması çalışırken, istemci hizmete istekler yapar ve ilgili bilgileri, yanıtlardan konsol penceresine yazar.

#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için

1. ASP.NET önbelleğe alma tümleştirme örneği için çözümü açın.

2. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.

3. **Çözüm Gezgini** pencere zaten açık DEĞILSE, CTRL + W + S tuşlarına basın.

4. **Çözüm Gezgini** penceresinden, **hizmet** projesine sağ tıklayın ve **Yeni örnek Başlat**' ı seçin. Bu, hizmeti barındıran ASP.NET geliştirme sunucusunu başlatır.

5. **Çözüm Gezgini** penceresinden, **istemci** projesine sağ tıklayın ve **Yeni örnek Başlat**' ı seçin.

6. İstemci Konsolu penceresi görünür ve çalışan hizmetin URI 'sini ve çalışan hizmet için HTML yardım sayfasının URI 'sini sağlar. Herhangi bir noktada, yardım sayfasının URI 'sini bir tarayıcıda yazarak HTML yardım sayfasını görüntüleyebilirsiniz.

7. Örnek çalışırken, istemci geçerli etkinliğin durumunu yazar.

8. İstemci konsol uygulamasını sonlandırmak için herhangi bir tuşa basın.

9. Hizmetin hata ayıklamasını durdurmak için SHIFT + F5 tuşlarına basın.

10. Windows bildirim alanında, ASP.NET Development Server simgesine sağ tıklayın ve **Durdur**' u seçin.
