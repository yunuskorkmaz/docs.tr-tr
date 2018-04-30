---
title: WCF Analiz İzleme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6029c7c7-3515-4d36-9d43-13e8f4971790
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 57e3ee18848031bce8ffbb54d26353fe36ee1def
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="wcf-analytic-tracing"></a>WCF Analiz İzleme
Bu örnek, kendi izleme olaylarını analitik akışının içine izlerini eklemek gösterilmiştir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ETW Yazar [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]. Analitik izlemeleri, yüksek performanslı cezası ödeme olmadan Hizmetleri içine görünürlük elde kolaylaştırmak için yöneliktir. Bu örnek nasıl kullanılacağını göstermektedir <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> API'leri ile tümleştirmenize yazma olayları [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri.  
  
 Hakkında daha fazla bilgi için <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> API'leri, bkz: <xref:System.Diagnostics.Eventing?displayProperty=nameWithType>.  
  
 Windows olay izleme hakkında daha fazla bilgi için bkz: [artırmak hata ayıklama ve performans ayarlama ETW ile](http://go.microsoft.com/fwlink/?LinkId=166488).  
  
## <a name="disposing-eventprovider"></a>EventProvider atma  
 Bu örnekte <xref:System.Diagnostics.Eventing.EventProvider?displayProperty=nameWithType> sınıfı, hangi uygulayan <xref:System.IDisposable?displayProperty=nameWithType>. İzlemeyi uygularken bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti, bunu kullanabilir, büyük olasılıkla <xref:System.Diagnostics.Eventing.EventProvider>ait hizmet ömrü için kaynaklar. Bu örnek hiçbir zaman bu nedenle ve Okunabilirlik için kaydırılmış siler. <xref:System.Diagnostics.Eventing.EventProvider>. Herhangi bir nedenden dolayı hizmetiniz farklı varsa, izleme ve gereksinimleri bu kaynağını atma gerekir ve bu örnek yönetilmeyen kaynaklarını atma yönelik en iyi uygulamaları uygun olarak değiştirmeniz gerekir. Yönetilmeyen kaynakları atma hakkında daha fazla bilgi için bkz: [Dispose yöntemi uygulama](http://go.microsoft.com/fwlink/?LinkId=166436).  
  
## <a name="self-hosting-vs-web-hosting"></a>Kendi kendine barındırma vs. Web barındırma  
 İçin Web barındırılan hizmetleri, WCF'ın analitik izlemeleri izleri yayma hizmeti tanımlamak için kullanılan "HostReference" adlı bir alan sağlar. Bu modelde, Genişletilebilir kullanıcı izlemeleri katılabilir ve bu örnek Bunun yapılması için en iyi uygulamaları gösterir. Bir Web ana bilgisayarı biçimi başvuru kanal '&#124;' karakteri gerçekte görünür kaynaklanan dize aşağıdakilerden herhangi biri olabilir:  
  
-   Uygulama kök dizininde değilse.  
  
     \<SiteName >\<ApplicationVirtualPath >&#124;\<ServiceVirtualPath >&#124;\<ServiceName >  
  
-   Uygulama kök dizininde ise.  
  
     \<SiteName >&#124;\<ServiceVirtualPath >&#124;\<ServiceName >  
  
 Kendini barındıran Hizmetleri için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]'s analitik izlemeleri "HostReference" alanını doldurmak değil. `WCFUserEventProvider` Sınıfı bu örnekteki davranır tutarlı bir kendi kendini barındıran hizmet tarafından kullanıldığında.  
  
## <a name="custom-event-details"></a>Özel olay ayrıntıları  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]kişinin ETW Olay sağlayıcısı bildirimini tanımlar tarafından gösterilen için tasarlanmış üç olayları [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yazarların hizmet kod içinde hizmet. Aşağıdaki tabloda, üç olayları dökümünü gösterir.  
  
|Olay|Açıklama|Olay Kimliği|  
|-----------|-----------------|--------------|  
|UserDefinedInformationEventOccurred|Şey not hizmetinizi içinde bir sorun olduğunda bu olay yayma. Örneğin, bir veritabanı çağrısı başarıyla yaptıktan sonra bir olay yayma.|301|  
|UserDefinedWarningOccurred|Bu yayma bir sorun ortaya çıktığında olay neden olabilir bir hata gelecekte. Örneğin, bir veritabanı için bir çağrı başarısız olur, ancak bir yedek veri deposuna geri dönmeden tarafından kurtarmanız mümkün olduğunda bir uyarı olayı yayabilir.|302|  
|UserDefinedErrorOccurred|Bu olay, hizmet beklendiği gibi davranır başarısız olduğunda yayma. Örneğin, bir olay bir veritabanı çağrısı başarısız olursa ve, verileri başka bir yerden alınamadı yayma.|303|  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], WCFAnalyticTracingExtensibility.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Çözümü çalıştırmak için CTRL + F5 tuşuna basın.  
  
     Web tarayıcısında tıklatın **Calculator.svc**. Hizmet için WSDL belgenin URI tarayıcıda görüntülenmesi gerekir. Bu URI kopyalayın.  
  
4.  Çalıştırma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test istemcisi (WcfTestClient.exe).  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Test istemcisi (WcfTestClient.exe) bulunduğu \< [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] yükleme dizini > \Common7\IDE\ WcfTestClient.exe (varsayılan [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] yükleme dizini olan C:\Program Files\Microsoft Visual Studio 10.0).  
  
5.  İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test istemci, hizmet seçerek eklemek **dosya**ve ardından **Hizmet Ekle**.  
  
     Uç nokta adresi giriş kutusuna ekleyin.  
  
6.  Tıklatın **Tamam** iletişim kutusunu kapatmak için.  
  
     ICalculator hizmeti altındaki sol bölmede eklenir **My hizmeti projeleri**.  
  
7.  Olay Görüntüleyicisi'ni uygulamasını açın.  
  
     Hizmet çağrılırken önce Olay Görüntüleyicisi'ni başlatın ve olay günlüğü olaylarını izleme alanından yayınlaması için dinleme yaptığından emin [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.  
  
8.  Gelen **Başlat** menüsünde, select **Yönetimsel Araçlar**ve ardından **Olay Görüntüleyicisi'ni**. Etkinleştirme **analitik** ve **hata ayıklama** günlükleri.  
  
9. Olay Görüntüleyicisi'nde ağaç görünümünde gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**ve ardından **Uygulama uygulamalarının**. Sağ **uygulama uygulamalarının**seçin **Görünüm**ve ardından **Analitik ve hata ayıklama günlüklerini göster**.  
  
     Emin **Analitik ve hata ayıklama günlüklerini göster** seçeneği denetlenir. Etkinleştirme **analitik** günlük.  
  
     Olay Görüntüleyicisi'nde ağaç görünümünde gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**,  **Uygulama sunucusu-uygulamalar**ve ardından **analitik**. Sağ **analitik** seçip **günlüğü etkinleştir**.  
  
10. WCF Test İstemcisi'ni kullanarak hizmetini sınayın.  
  
    1.  WCF Test istemcisi **Add()** ICalculator Hizmeti düğümü altındaki.  
  
         **Add()** yöntemi iki parametrelerle sağ bölmede görünür.  
  
    2.  İlk parametresi için 2 ve 3 ikinci parametre için yazın.  
  
    3.  Tıklatın **Invoke** yöntemini çağırmak için.  
  
11. Git **Olay Görüntüleyicisi'ni** zaten açık penceresi. Gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, **uygulama Sunucu uygulamaları**.  
  
12. Sağ **analitik** düğümü ve select **yenileme**.  
  
     Olayları sağ bölmede görüntülenir.  
  
13. Olay Kimliği 303 bulun ve dosyayı açın ve içeriğini incelemek için çift tıklayın.  
  
     Bu olay tarafından gösterilen `Add()` ICalculator hizmetinin yöntemi ve eşit bir yükü sahip "2 + 3 = 5".  
  
#### <a name="to-clean-up-optional"></a>(İsteğe bağlı) temizlemek için  
  
1.  Açık **Olay Görüntüleyicisi'ni**.  
  
2.  Gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**ve ardından  **Uygulama sunucusu uygulamalar**. Sağ **analitik** seçip **günlüğü devre dışı**.  
  
3.  Gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**,  **Uygulama sunucusu uygulamalar**ve ardından **analitik**. Sağ **analitik** seçip **Günlüğü Temizle**.  
  
4.  Tıklatın **temizleyin** olayları temizleyin.  
  
## <a name="known-issue"></a>Bilinen bir sorun  
 Bilinen bir sorun var. **Olay Görüntüleyicisi'ni** burada da başarısız olabilir ETW olayları çözecek. Bildiren bir hata iletisi görebilirsiniz: "olay kimliği için açıklama \<kimliği > kaynağından Microsoft Windows uygulaması uygulamalarının bulunamıyor. Bu olayı oluşturan bileşen, yerel bilgisayarda yüklü değil ya da yüklemesi bozuk. Yükleyebilir veya yerel bilgisayarda bileşen onarın." Bu hatayla karşılaşırsanız, seçin **yenileme** gelen **Eylemler** menüsü. Olay sonra düzgün bir şekilde kod çözme.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTrace`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric izleme örnekleri](http://go.microsoft.com/fwlink/?LinkId=193959)
