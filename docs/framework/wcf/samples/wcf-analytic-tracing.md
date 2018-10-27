---
title: WCF Analiz İzleme
ms.date: 03/30/2017
ms.assetid: 6029c7c7-3515-4d36-9d43-13e8f4971790
ms.openlocfilehash: a5e4b82bd28cae18f393a4143325623634d4bbaf
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50181663"
---
# <a name="wcf-analytic-tracing"></a>WCF Analiz İzleme
Bu örnek ETW Windows Communication Foundation (WCF) Yazar analitik izlemeleri akışının içine kendi izleme olaylarını ekleme gösterir [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]. Analitik izlemeleri, yüksek performans cezası ödeme yapmadan hizmetlerinizi görünürlük elde etmek kolay hale getirmek için yöneliktir. Bu örnek nasıl kullanılacağını gösterir <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> API WCF hizmetleri ile tümleştirme yazma olayları.  
  
 Hakkında daha fazla bilgi için <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> API'leri bkz <xref:System.Diagnostics.Eventing?displayProperty=nameWithType>.  
  
 Windows olay izleme hakkında daha fazla bilgi için bkz: [artırmak hata ayıklama ve performans ayarlama ETW ile](https://go.microsoft.com/fwlink/?LinkId=166488).  
  
## <a name="disposing-eventprovider"></a>EventProvider disposing  
 Bu örnekte <xref:System.Diagnostics.Eventing.EventProvider?displayProperty=nameWithType> sınıfını <xref:System.IDisposable?displayProperty=nameWithType>. Bir WCF hizmeti için izleme uygularken, kullanabileceğiniz olası <xref:System.Diagnostics.Eventing.EventProvider>ait hizmet ömrü için kaynaklar. Bu nedenle ve Okunabilirlik için bu örneği hiçbir zaman Sarmalanan siler <xref:System.Diagnostics.Eventing.EventProvider>. Herhangi bir nedenle farklı hizmetiniz varsa, bu kaynağın izleme ve gereksinimleri dispose gerekir ve bu örnek yönetilmeyen kaynaklarını atma için en iyi uygun olarak değiştirmeniz gerekir. Yönetilmeyen kaynakların elden hakkında daha fazla bilgi için bkz. [Implementing a Dispose Method](https://go.microsoft.com/fwlink/?LinkId=166436).  
  
## <a name="self-hosting-vs-web-hosting"></a>Kendi kendine barındırma vs. Web barındırma  
 Web barındırılan hizmetler için WCF'ın analitik izlemeleri izlemeleri yayma hizmeti tanımlamak için kullanılan "HostReference" adlı bir alan sağlar. Bu modelde, Genişletilebilir kullanıcı izlemeleri katılabilir ve bu örnek, bunu yapmak için en iyi uygulamaları gösterir. Bir Web ana bilgisayarı biçimi başvuru kanal '&#124;' karakter gerçekten görünür ortaya çıkan dize, aşağıdakilerden herhangi biri olabilir:  
  
-   Uygulama kök dizininde değilse.  
  
     \<SiteName >\<ApplicationVirtualPath >&#124;\<ServiceVirtualPath >&#124;\<ServiceName >  
  
-   Uygulama kök dizininde ise.  
  
     \<SiteName >&#124;\<ServiceVirtualPath >&#124;\<ServiceName >  
  
 Şirket içinde barındırılan hizmetler için WCF'ın analitik izlemeleri "HostReference" alanı doldurmayın. `WCFUserEventProvider` Bu örnekteki sınıf davranışını tutarlı bir şekilde şirket içinde barındırılan bir hizmet tarafından kullanıldığında.  
  
## <a name="custom-event-details"></a>Özel olay ayrıntıları  
 WCF'ın ETW Olay sağlayıcısı bildirimi hizmeti kodundaki WCF Hizmeti yazarlar tarafından yayılan için tasarlanmış üç olayları tanımlar. Aşağıdaki tabloda, üç olay dökümünü gösterir.  
  
|Olay|Açıklama|Olay Kimliği|  
|-----------|-----------------|--------------|  
|UserDefinedInformationEventOccurred|Bu olay bir notun hizmetinizdeki bir sorun meydana geldiğinde gösterin. Örneğin, bir veritabanı çağrısı yapıldıktan sonra bir olay yayabilir.|301|  
|UserDefinedWarningOccurred|Bu yayma, bir sorun oluştuğunda, olay bir hataya neden gelecekte. Örneğin, bir veritabanına bir çağrı başarısız olur, ancak bir veri deposuna dönülüyor tarafından kurtarmanız mümkün olduğunda bir uyarı olayı yayabilir.|302|  
|UserDefinedErrorOccurred|Hizmetinizi beklendiği gibi davranmaya başarısız olduğunda bu olay gösterin. Örneğin, bir olay veritabanına bir çağrı başarısız olursa ve, verileri başka bir yerden alınamadı yayabilir.|303|  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Visual Studio 2012 kullanarak WCFAnalyticTracingExtensibility.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.  
  
     Web tarayıcısında tıklayın **Calculator.svc**. WSDL belgesinde hizmet URI'si tarayıcı içinde görüntülenmesi gerekir. Bu URI'yi kopyalayın.  
  
4.  WCF test istemcisi (WcfTestClient.exe) çalıştırın.  
  
     WCF test istemcisi (WcfTestClient.exe) şu konumdadır `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`. Varsayılan Visual Studio 2012 yükleme dizini olan `C:\Program Files\Microsoft Visual Studio 10.0`.  
  
5.  WCF test istemcisi içinde hizmet seçerek ekleyin **dosya**, ardından **Hizmet Ekle**.  
  
     Uç nokta adresi giriş kutusuna ekleyin.  
  
6.  Tıklayın **Tamam** iletişim kutusunu kapatmak için.  
  
     Sol bölmede altında ICalculator hizmet eklenir **hizmet Projelerim**.  
  
7.  Olay Görüntüleyici uygulamasını açın.  
  
     Hizmetini çağırmak önce Olay Görüntüleyicisi'ni başlatın ve olay günlüğüne olayları WCF hizmetinden yayılan izleme dinlediğinden emin olun.  
  
8.  Gelen **Başlat** menüsünde **Yönetimsel Araçlar**, ardından **Olay Görüntüleyicisi'ni**. Etkinleştirme **analitik** ve **hata ayıklama** günlükleri.  
  
9. Olay Görüntüleyicisi'nde ağaç görünümünde gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**ve ardından **Uygulama uygulamalarının**. Sağ **uygulama uygulamalarının**seçin **görünümü**, ardından **Analitik ve hata ayıklama günlüklerini göster**.  
  
     Emin **Analitik ve hata ayıklama günlüklerini göster** seçeneği denetlenir. Etkinleştirme **analitik** günlük.  
  
     Olay Görüntüleyicisi'nde ağaç görünümünde gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**,  **Uygulama uygulamalarının**, ardından **analitik**. Sağ **analitik** seçip **günlüğü etkinleştir**.  
  
10. WCF Test İstemcisi'ı kullanarak hizmeti test edin.  
  
    1.  WCF Test İstemcisi'nde çift **Add()** ICalculator hizmet düğümü altında.  
  
         **Add()** yöntemi sağ bölmede iki parametre ile görünür.  
  
    2.  İlk parametresi için 2 ve 3 ' İkinci parametre için yazın.  
  
    3.  Tıklayın **Invoke** yöntemini çağırmak için.  
  
11. Git **Olay Görüntüleyicisi'ni** zaten açık bir pencere. Gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, **uygulama Sunucu uygulamaları**.  
  
12. Sağ **analitik** düğümünü seçip alt **Yenile**.  
  
     Olaylar, sağ bölmede görüntülenir.  
  
13. 303 kimlik olayla bulun ve dosyayı açın ve içeriğini incelemek için çift tıklayın.  
  
     Bu olay tarafından izlenemiyor `Add()` ICalculator hizmetinin yöntemi ve bir yükü eşit "2 + 3 = 5".  
  
#### <a name="to-clean-up-optional"></a>(İsteğe bağlı) temizlemek için  
  
1.  Açık **Olay Görüntüleyicisi'ni**.  
  
2.  Gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, ardından  **Uygulama sunucusu uygulamalar**. Sağ **analitik** seçip **devre dışı günlük**.  
  
3.  Gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**,  **Uygulama sunucu uygulamaları**, ardından **analitik**. Sağ **analitik** seçip **Günlüğü Temizle**.  
  
4.  Tıklayın **Temizle** olayları temizleyin.  
  
## <a name="known-issue"></a>Bilinen sorun  
 Bilinen bir sorun var. **Olay Görüntüleyicisi'ni** burada da başarısız olabilir ETW olaylarının kodunu çözmek. Bildiren bir hata iletisini görebilirsiniz: "olay kimliği için açıklama \<kimliği > kaynağından Microsoft Windows uygulaması uygulamalarının nebyla nalezena. Bu olayı oluşturan bileşen, yerel bilgisayarınızda yüklü değil veya yüklemenin bozuk. Yükleyebilir veya yerel bilgisayarda bileşen onarın." Bu hatayla karşılaşırsanız, seçin **Yenile** gelen **eylemleri** menüsü. Olay sonra düzgün bir şekilde kod çözme.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTrace`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric izleme örnekleri](https://go.microsoft.com/fwlink/?LinkId=193959)
