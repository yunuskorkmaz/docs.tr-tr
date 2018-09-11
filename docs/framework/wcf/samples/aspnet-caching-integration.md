---
title: ASP.NET Önbelleğe Alma Tümleştirmesi
ms.date: 03/30/2017
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
ms.openlocfilehash: 55e6213bf0c4c212ebcf4e68882d16532c0e4229
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44353583"
---
# <a name="aspnet-caching-integration"></a>ASP.NET Önbelleğe Alma Tümleştirmesi
Bu örnek, WCF WEB HTTP programlama modeli ile ASP.NET çıktı önbelleği nasıl gösterir. Lütfen [temel kaynak hizmeti](../../../../docs/framework/wcf/samples/basic-resource-service.md) derinliği hizmet uygulamasında anlatılmaktadır bu senaryo, şirket içinde barındırılan bir sürümü için örnek. Bu konu, ASP.NET çıktı önbelleği tümleştirme özelliği üzerinde odaklanır.  
  
## <a name="demonstrates"></a>Gösteriler  
 ASP.NET çıktı önbelleği ile tümleştirme  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`  
  
## <a name="discussion"></a>Tartışma  
 Örnek kullanır <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> ASP.NET kullanmaya çıktı Windows Communication Foundation (WCF) hizmetiyle önbelleği. <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> Hizmet işlemleri için uygulanır ve yanıtlarını belirtilen işlemi uygulanması gereken yapılandırma dosyasında bir önbellek profili adını sağlar.  
  
 Örnek hizmet projesinin adını da dosyasında hem `GetCustomer` ve `GetCustomers` işlemleri ile işaretlenir <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, önbellek profili adı "CacheFor60Seconds" sağlar. Hizmet projesinin Web.config dosyasının önbellek profili "CacheFor60Seconds" kapsamında sağlanır <`caching`> öğesi <`system.web`>. Bu önbellek profili değeri için `duration` özniteliktir "60" şekilde bu profil ile ilişkili yanıtları ASP.NET çıktı önbelleğinde 60 saniye için önbelleğe alınır. Ayrıca, bu önbellek profili için `varmByParam` "için farklı değerlerle bunu isteklerini biçimlendirmek için" özniteliği ayarlanmış `format` sorgu dizesi parametresi yanıtlarını ayrı olarak önbelleğe sahip. Son olarak, önbellek profilin `varyByHeader` özniteliği "Kabul et" olarak ayarlanmışsa, farklı bir Accept üstbilgi değerlerini isteklerle yanıtlarını ayrı olarak önbelleğe alacak şekilde.  
  
 İstemci projesindeki program.cs gösterir böyle bir istemci nasıl olabileceğini kullanılarak yazılan <xref:System.Net.HttpWebRequest>. Bir WCF Hizmeti erişmek için yalnızca bir yol olduğunu unutmayın. WCF kanal fabrikası gibi diğer .NET Framework sınıflarını kullanarak hizmete erişmek mümkündür ve <xref:System.Net.WebClient>. SDK diğer örnekleri (gibi [temel HTTP hizmeti](../../../../docs/framework/wcf/samples/basic-http-service.md) örnek ve [Otomatik Biçim Seçimi](../../../../docs/framework/wcf/samples/automatic-format-selection.md) örnek) bu sınıfların bir WCF Hizmeti ile iletişim için nasıl kullanılacağını göstermektedir.  
  
## <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
 Örnek üç projelerin oluşur:  
  
-   **Hizmet**: ASP.NET barındırılan bir WCF HTTP hizmetini içeren bir Web uygulaması projesi.  
  
-   **İstemci**: hizmetine çağrı yapan bir konsol uygulama projesi.  
  
-   **Ortak**: hizmet ve istemci tarafından kullanılan müşteri türü içeren paylaşılan bir kitaplık.  
  
 İstemci konsol uygulaması çalışırken istemci hizmete isteği yapan ve konsol penceresine yanıtlardan bilgileri yazar.  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  ASP.NET önbelleğe alma tümleştirmesi için örnek çözümü açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Varsa **Çözüm Gezgini** pencere zaten açık değilse, CTRL + W + S tuşuna basın.  
  
4.  Gelen **Çözüm Gezgini** penceresinde, sağ tıklama **hizmet** seçin ve proje **yeni örnek Başlat**. Bu, hizmeti barındıran ASP.NET geliştirme sunucusu başlatır.  
  
5.  Gelen **Çözüm Gezgini** penceresinde, sağ tıklama **istemci** seçin ve proje **yeni örnek Başlat**.  
  
6.  İstemci konsol penceresi görünür ve çalışan hizmetin URI sağlar ve URI HTML Yardım sayfası çalışan hizmeti. Herhangi bir noktada HTML Yardım sayfası URI Yardım sayfasının bir tarayıcıda yazarak görüntüleyebilirsiniz.  
  
7.  Örnek çalışırken, istemcinin geçerli etkinlik durumunu yazar.  
  
8.  İstemci Konsolu uygulamayı sonlandırmak için herhangi bir tuşa basın.  
  
9. Hizmet hata ayıklamayı durdurmak için SHIFT + F5 tuşlarına basın.  
  
10. Windows bildirim alanındaki ASP.NET Geliştirme Sunucusu simgesine sağ tıklayın ve seçin **Durdur**.
