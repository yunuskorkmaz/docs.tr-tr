---
title: WCF Analiz İzleme
ms.date: 03/30/2017
ms.assetid: 6029c7c7-3515-4d36-9d43-13e8f4971790
ms.openlocfilehash: ef636a672d9384e8e3d658f0488cfaadb8d293e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183227"
---
# <a name="wcf-analytic-tracing"></a>WCF Analiz İzleme
Bu örnek, Windows Communication Foundation'ın (WCF) ETW'ye yazdığı analitik izleme akışına [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]kendi izleme etkinliklerinizi nasıl ekleyeceğinizi göstermektedir. Analitik izlemeler, yüksek performans cezası ödemeden hizmetlerinizin görünürlüğünü kolaylaştırmayı amaçlıyor. Bu örnek, WCF <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> hizmetleriyle tümleşen olayları yazmak için API'lerin nasıl kullanılacağını gösterir.  
  
 API'ler <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> hakkında daha <xref:System.Diagnostics.Eventing?displayProperty=nameWithType>fazla bilgi için bkz.  
  
 Windows'da olay izleme hakkında daha fazla bilgi edinmek için [ETW ile Hata Ayıklama ve Performans Alanına İyileşin](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw)bölümüne bakın.  
  
## <a name="disposing-eventprovider"></a>EventProvider'ı Ortadan Keleme  
 Bu örnek, <xref:System.Diagnostics.Eventing.EventProvider?displayProperty=nameWithType> uygular sınıf <xref:System.IDisposable?displayProperty=nameWithType>kullanır. Bir WCF hizmeti için izleme uygularken, <xref:System.Diagnostics.Eventing.EventProvider>'kaynakları hizmetin ömrü boyunca kullanabilirsiniz. Bu nedenle, ve okunabilirlik için, bu örnek sarılmış <xref:System.Diagnostics.Eventing.EventProvider>asla atraz. Herhangi bir nedenle hizmetinizin izleme için farklı gereksinimleri varsa ve bu kaynağı elden çıkarmanız gerekiyorsa, bu örneği yönetilmeyen kaynakları atmak için en iyi uygulamalara uygun olarak değiştirmeniz gerekir. Yönetilmeyen kaynakların atılması hakkında daha fazla bilgi için [bkz.](https://docs.microsoft.com/dotnet/standard/garbage-collection/implementing-dispose)  
  
## <a name="self-hosting-vs-web-hosting"></a>Self-Hosting vs Web Hosting  
 Web tarafından barındırılan hizmetler için WCF'nin analitik izlemeleri, izleri yayan hizmeti tanımlamak için kullanılan "HostReference" adlı bir alan sağlar. Genişletilebilir kullanıcı izleri bu modele katılabilir ve bu örnek bunu yapmak için en iyi uygulamaları gösterir. '&#124;' bölümü aslında ortaya çıkan dizede göründüğünde web ana bilgisayar başvurusu biçimi aşağıdakilerden biri olabilir:  
  
- Uygulama kökünde değilse.  
  
     \<SiteName \<>UygulamasıVirtualPath>&#124;\< \<ServisiVirtualPath>&#124;ServiceName>  
  
- Uygulama kökünde yse.  
  
     \<SiteAdı \<>&#124;ServisiVirtualPath>&#124;\<ServisiAd>  
  
 Kendi kendine barındırılan hizmetler için WCF'nin analitik izleri "HostReference" alanını doldurmaz. Bu `WCFUserEventProvider` örnekteki sınıf, kendi barındırılan bir hizmet tarafından kullanıldığında tutarlı bir şekilde kullanılır.  
  
## <a name="custom-event-details"></a>Özel Etkinlik Ayrıntıları  
 WCF'nin ETW Olay Sağlayıcısı bildirimi, WCF hizmet yazarları tarafından hizmet kodu içinden yayılacak şekilde tasarlanmış üç olayı tanımlar. Aşağıdaki tabloda üç olayın dökümü gösterilmektedir.  
  
|Olay|Açıklama|Olay Kimliği|  
|-----------|-----------------|--------------|  
|UserDefinedInformationEventOccurred|Bu olayı, hizmetinizde sorun olmayan bir şey olduğunda yayınız. Örneğin, veritabanına başarılı bir şekilde arama yaptıktan sonra bir olay yarayabilirsiniz.|301|  
|UserDefinedWarningOluştu|Gelecekte bir hataya neden olabilecek bir sorun oluştuğunda bu olayı yayıştırın. Örneğin, bir veritabanına yapılan bir çağrı başarısız olduğunda ancak gereksiz bir veri deposuna geri dönerek kurtarabilirsiniz.|302|  
|UserDefinedErrorOccurred|Hizmetiniz beklendiği gibi şekilde çalışmadığında bu olayı yayış. Örneğin, veritabanına yapılan bir çağrı başarısız olursa ve verileri başka bir yerden alamayınca bir olay yayık olabilirsiniz.|303|  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1. Visual Studio 2012'yi kullanarak WCFAnalyticTracingExtensibility.sln çözüm dosyasını açın.  
  
2. Çözümü oluşturmak için CTRL+SHIFT+B tuşuna basın.  
  
3. Çözümü çalıştırmak için CTRL+F5 tuşuna basın.  
  
     Web tarayıcısında, **Calculator.svc'yi**tıklatın. Hizmet için WSDL belgesinin URI tarayıcıda görünmelidir. Uri'yi kopyala.  
  
4. WCF test istemcisini çalıştırın (WcfTestClient.exe).  
  
     WCF test istemcisi (WcfTestClient.exe) `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`adresinde yer alır. Varsayılan Visual Studio 2012 `C:\Program Files\Microsoft Visual Studio 10.0`yüklemek dir .  
  
5. WCF test istemcisi içinde, **Dosya**seçerek hizmet ekleyin ve sonra **Hizmet ekle**.  
  
     Giriş kutusuna bitiş noktası adresini ekleyin.  
  
6. İletişim kutusunu kapatmak için **Tamam'ı** tıklatın.  
  
     ICalculator **hizmeti, Hizmet Projelerim**altında sol bölmeye eklenir.  
  
7. Olay Görüntüleyicisi uygulamasını açın.  
  
     Hizmeti başlatmadan önce Olay Görüntüleyicisi'ni başlatın ve olay günlüğünün WCF hizmetinden yayılan olayları izlemek için dinlediğinden emin olun.  
  
8. **Başlat** menüsünden **Yönetim Araçları'nı**ve ardından **Olay Görüntüleyicisi'ni**seçin. **Analitik** ve **Hata Ayıklama** günlüklerini etkinleştirin.  
  
9. Olay Görüntüleyici'deki ağaç görünümünde, **Olay Görüntüleyicisi,** **Uygulamalar ve Hizmetler Günlükleri,** **Microsoft,** **Windows**ve ardından **Uygulama Sunucusu-Uygulamaları'na**gidin. **Uygulama Sunucusu Uygulamaları'nı**sağ tıklatın, **Görünüm'i**seçin ve ardından Analitik ve **Hata Ayıklama Günlüklerini Göster'i**seçin.  
  
     **Analitik ve Hata Ayıklama Günlükleri'ni göster** seçeneğinin işaretli olduğundan emin olun. **Analitik** günlüğünü etkinleştirin.  
  
     Olay Görüntüleyici'deki ağaç görünümünde, **Olay Görüntüleyicisi,** **Uygulamalar ve Hizmetler Günlükleri,** **Microsoft,** **Windows,** **Application Server-Applications**, ve ardından **Analitik'** e gidin. **Analytic'e** sağ tıklayın ve **Günlüğü Etkinleştir'i**seçin.  
  
10. WCF Test İstemci'sini kullanarak hizmeti test edin.  
  
    1. WCF Test İstemci'sinde, ICalculator hizmet düğümünün altında **Add()** seçeneğini çift tıklatın.  
  
         **Ekle()** yöntemi iki parametre ile sağ bölmede görünür.  
  
    2. İlk parametre için 2, ikinci parametre için 3 yazın.  
  
    3. Yöntemi çağırmak için **Çağır'ı** tıklatın.  
  
11. Daha önce açtığınız **Olay Görüntüleyicisi** penceresine gidin. Olay **Görüntüleyici,** **Uygulamalar ve Hizmetler Günlükleri,** **Microsoft,** **Windows**, **Uygulama Sunucusu-Uygulamalar**gidin.  
  
12. **Analitik** düğüme sağ tıklayın ve **Yenile'yi**seçin.  
  
     Olaylar sağ bölmede görünür.  
  
13. 303 kimliği ile olay bulun ve açmak ve içeriğini incelemek için çift tıklayın.  
  
     Bu olay ICalculator hizmeti `Add()` yöntemi ile yayılan ve "2+3=5" eşit bir yüke sahiptir.  
  
#### <a name="to-clean-up-optional"></a>Temizlemek için (İsteğe Bağlı)  
  
1. **Olay Görüntüleyicisi**'ni açın.  
  
2. Olay **Görüntüleyici,** **Uygulamalar ve Hizmetler Günlükleri,** **Microsoft,** **Windows**ve ardından **Uygulama-Sunucu Uygulamaları**gidin. **Analytic'e** sağ tıklayın ve **Günlük'ünü Devre Dışı Nı**seçin.  
  
3. Olay **Görüntüleyici,** **Uygulamalar ve Hizmetler Günlükleri,** **Microsoft,** **Windows,** **Application-Server-Applications**, ve sonra **Analitik**gidin. **Analytic'e** sağ tıklayın ve **Günlük'u temizle'yi**seçin.  
  
4. Olayları temizlemek için **Temizle'yi** tıklatın.  
  
## <a name="known-issue"></a>Bilinen Sorun  
 **Olay Görüntüleyicisi'nde,** ETW olaylarının şifresini çözemediği bilinen bir sorun vardır. Şöyle bir hata iletisi görebilirsiniz: "Kaynakmicrosoft-Windows-Application Server-Applications'dan> Olay Kimliği \<kimliği açıklaması bulunamıyor. Bu olayı yükselten bileşen yerel bilgisayarınıza yüklenmez veya yükleme bozuk. Bileşeni yerel bilgisayara yükleyebilir veya onarabilirsiniz." Bu hatayla karşılaşırsanız, **Eylemler** menüsünden **Yenile'yi** seçin. Olay daha sonra düzgün bir şekilde deşifre edilmelidir.  
  
> [!IMPORTANT]
> Örnekler bilgisayarınıza zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTrace`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric İzleme Örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
