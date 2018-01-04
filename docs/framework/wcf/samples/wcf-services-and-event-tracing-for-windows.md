---
title: "Windows için WCF Hizmetleri ve Etkinlik İzleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cb8924cc04442e3b9eda5e251e6dcdc57f5660c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-services-and-event-tracing-for-windows"></a>Windows için WCF Hizmetleri ve Etkinlik İzleme
Bu örnek analitik izlemede kullanmak gösterilmiştir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] olayları, olay izleme için Windows (ETW) verebilmelidir. Analitik izlemeleri anahtar noktalarında yayılan olaylardır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] , sorun giderme izin yığın [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] üretim ortamında Hizmetleri.  
  
 Analitik izlemede [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri, izleme açılabilir bir üretim ortamında performansı üzerinde en az etkiyle. Bu izlemeler olayları ETW oturumuna olarak gösterilen.  
  
 Bu örnek temel içeren [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hangi olayların hizmetinden Olay Görüntüleyicisi kullanılarak görüntülenebilir olay günlüğü için gösterilen hizmeti. Olayları dinler adanmış bir ETW oturumu başlatmak mümkündür [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet. Örnek olayları Olay Görüntüleyicisi'ni kullanarak okunabilir ikili bir dosyada depolar adanmış bir ETW oturum oluşturmak için bir komut dosyası içerir.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], EtwAnalyticTraceSample.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Çözümü çalıştırmak için CTRL + F5 tuşuna basın.  
  
     Web tarayıcısında tıklatın **Calculator.svc**. Hizmet için WSDL belgenin URI tarayıcıda görüntülenmesi gerekir. Bu URI kopyalayın.  
  
     Varsayılan olarak, bağlantı noktası 1378 (http://localhost:1378/Calculator.svc) isteklerini dinleme hizmetini başlatır.  
  
4.  Çalıştırma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test istemcisi (WcfTestClient.exe).  
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Test istemcisi (WcfTestClient.exe) bulunduğu \< [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] yükleme dizini > \Common7\IDE\ WcfTestClient.exe (varsayılan [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] yükleme dizini olan C:\Program Files\Microsoft Visual Studio 10.0).  
  
5.  İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test istemci, hizmet seçerek eklemek **dosya**ve ardından **Hizmet Ekle**.  
  
     Uç nokta adresi giriş kutusuna ekleyin. Http://localhost:1378/Calculator.svc varsayılandır.  
  
6.  Olay Görüntüleyicisi'ni uygulamasını açın.  
  
     Hizmet çağrılırken önce Olay Görüntüleyicisi'ni başlatın ve olay günlüğü olaylarını izleme alanından yayınlaması için dinleme yaptığından emin [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.  
  
7.  Gelen **Başlat** menüsünde, select **Yönetimsel Araçlar**ve ardından **Olay Görüntüleyicisi'ni**.  Etkinleştirme **analitik** ve **hata ayıklama** günlükleri.  
  
8.  Olay Görüntüleyicisi'nde ağaç görünümünde gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**ve ardından **Uygulama uygulamalarının**. Sağ **uygulama uygulamalarının**seçin **Görünüm**ve ardından **Analitik ve hata ayıklama günlüklerini göster**.  
  
     Emin **Analitik ve hata ayıklama günlüklerini göster** seçeneği denetlenir.  
  
9. Etkinleştirme **analitik** günlük.  
  
     Olay Görüntüleyicisi'nde ağaç görünümünde gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**ve ardından **Uygulama uygulamalarının**. Sağ **analitik** seçip **günlüğü etkinleştir**.  
  
#### <a name="to-test-the-service"></a>Hizmeti sınamak için  
  
1.  Dönmek [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çift tıklayın ve test istemcisi `Divide` ve Payda 0 belirtin varsayılan değerleri koruyun.  
  
     Paydanın 0 ise, hizmet bir hata oluşturur.  
  
2.  Hizmetinden gösterilen olayları gözlemektir.  
  
     Olay Görüntüleyici'ye geçiş yapın ve gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**ve ardından **Uygulama uygulamalarının**. Sağ **analitik** seçip **yenileme**.  
  
     WCF analiz izleme olayları Olay Görüntüleyicisi'nde görüntülenir. Bir arıza tarafından oluşturulan olduğundan hizmet bir hata izleme olayı olduğundan Olay Görüntüleyicisi görüntülenen dikkat edin.  
  
3.  1 ve 2, ancak geçerli giriş ile. Değeri `N2` parametresi, 0 dışında herhangi bir sayı olabilir.  
  
     WCF görüntülemek için analitik kanal yenileme olayları hata olaylarını içermez.  
  
 Örnek bir WCF hizmetinden yayılan analitik izleme olayları gösterir.  
  
#### <a name="to-cleanup-optional"></a>Temizleme (isteğe bağlı)  
  
1.  Olay Görüntüleyicisi'ni açın.  
  
2.  Gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**ve ardından  **Uygulama sunucusu uygulamalar**. Sağ **analitik** seçip **günlüğü devre dışı**.  
  
3.  Gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**ve ardından  **Uygulama sunucusu uygulamalar**. Sağ **analitik** seçip **Günlüğü Temizle**.  
  
4.  Seçin **temizleyin** olayları temizlemek için seçeneği.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric izleme örnekleri](http://go.microsoft.com/fwlink/?LinkId=193959)
