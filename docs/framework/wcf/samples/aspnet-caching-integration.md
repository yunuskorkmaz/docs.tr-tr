---
title: ASP.NET Önbelleğe Alma Tümleştirmesi
ms.date: 03/30/2017
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
ms.openlocfilehash: 744ecbff8b51565906ff4c619ba8c8aecff123c7
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33805414"
---
# <a name="aspnet-caching-integration"></a>ASP.NET Önbelleğe Alma Tümleştirmesi
Bu örnek, ASP.NET çıktı önbelleğine WCF WEB HTTP programlama modeli kullanan gösterilmiştir. Lütfen bakın [temel kaynak hizmeti](../../../../docs/framework/wcf/samples/basic-resource-service.md) kendini barındıran sürümü derinliği hizmet uygulamasında ele bu senaryo için örnek. Bu konu ASP.NET çıktı önbelleği tümleştirme özelliğini odaklanır.  
  
## <a name="demonstrates"></a>Gösteriler  
 ASP.NET çıktı önbelleği ile tümleştirme  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`  
  
## <a name="discussion"></a>Tartışma  
 Örnek kullanır <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> ASP.NET faydalanmak için Windows Communication Foundation (WCF) hizmetiyle önbelleğe alma çıktı. <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> Hizmet işlemleri için uygulanır ve yanıtlarını verilen işlemi uygulanması gereken yapılandırma dosyasında bir önbellek profili adı sağlar.  
  
 Örnek hizmet projesinin adını da dosyasındaki hem `GetCustomer` ve `GetCustomers` işlemleri ile işaretlenmiş <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, önbellek profili adı "CacheFor60Seconds" sağlar. Hizmet projesinin Web.config dosyasında önbellek profili "CacheFor60Seconds" altında sağlanır <`caching`> öğesi <`system.web`>. Bu önbellek profili değeri için `duration` özniteliktir "60", bu profil ile ilişkili ASP.NET çıktı önbelleği 60 saniye boyunca önbelleğe alınan yanıtları şekilde. Ayrıca, bu önbellek profili için `varmByParam` özniteliği ayarlanmış "için farklı değerler bunu istekleriyle biçim" `format` sorgu dizesi parametresi ayrı olarak önbelleğe yanıtlarını sahip. Son olarak, önbellek profilinin `varyByHeader` özniteliği, "Kabul et" ayarlanmışsa, farklı Accept üstbilgi değerlerini istekleriyle yanıtlarını ayrı olarak önbelleğe alacak şekilde.  
  
 İstemci projesindeki program.cs gösteren böyle bir istemci nasıl olabilir kullanılarak yazılan <xref:System.Net.HttpWebRequest>. Bu bir WCF Hizmeti erişmenin tek yolu olduğuna dikkat edin. WCF kanal fabrikası gibi diğer .NET Framework sınıfları kullanarak hizmete erişmek mümkündür ve <xref:System.Net.WebClient>. SDK'sındaki diğer örnekleri (gibi [temel HTTP hizmeti](../../../../docs/framework/wcf/samples/basic-http-service.md) örnek ve [Otomatik Biçim Seçimi](../../../../docs/framework/wcf/samples/automatic-format-selection.md) örnek) bu sınıfların bir WCF Hizmeti ile iletişim için nasıl kullanılacağı gösterilmektedir.  
  
## <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
 Örnek üç projelerin oluşur:  
  
-   **Hizmet**: ASP.NET barındırılan bir WCF HTTP hizmeti içeren bir Web uygulaması projesi.  
  
-   **İstemci**: hizmet çağrılar bir konsol uygulama projesi.  
  
-   **Ortak**: istemci ve hizmet tarafından kullanılan müşteri türünü içeren paylaşılan bir kitaplık.  
  
 İstemci konsol uygulaması çalışırken, istemci hizmete istek yaptığında ve konsol penceresine yanıtlardan bilgileri yazar.  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  ASP.NET önbelleğe alma tümleştirmesi için örnek çözümü açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Varsa **Çözüm Gezgini** penceresi zaten açık, CTRL + W + S tuşlarına basın.  
  
4.  Gelen **Çözüm Gezgini** penceresinde, sağ tıklatma **hizmet** proje ve seçin **Başlat yeni örnek**. Bu hizmeti barındıran ASP.NET geliştirme sunucusu başlatır.  
  
5.  Gelen **Çözüm Gezgini** penceresinde, sağ tıklatma **istemci** proje ve seçin **Başlat yeni örnek**.  
  
6.  İstemci konsol penceresi görüntülenir ve çalışan hizmetin URI sağlar ve URI HTML sayfası çalışan hizmetin için yardımcı olur. Herhangi bir noktada, HTML Yardım sayfasına bir tarayıcıda yardım sayfasına URI'sini yazarak görüntüleyebilirsiniz.  
  
7.  Örnek çalışırken, istemcinin geçerli etkinlik durumunu yazar.  
  
8.  İstemci konsol uygulaması sonlandırmak için herhangi bir tuşa basın.  
  
9. Hata ayıklama hizmetini durdurmak için SHIFT + F5 tuşuna basın.  
  
10. Windows bildirim alanında ASP.NET Geliştirme Sunucusu simgesini sağ tıklatın ve seçin **durdurmak**.
