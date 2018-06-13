---
title: Windows için WCF Hizmetleri ve Etkinlik İzleme
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: ea917ee87b598fc3ad01df70d9aedfadfd1396a4
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809839"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a>Windows için WCF Hizmetleri ve Etkinlik İzleme
Bu örnek çözümleme izleme Windows Communication Foundation (WCF) olayları, olay izleme için Windows (ETW) yayma için nasıl kullanılacağını gösterir. Analitik izlemeleri, WCF hizmetleri üretim ortamında sorun giderme sağlayan anahtar noktalarda WCF yığınında gösterilen olaylardır.  
  
 WCF hizmetlerinde çözümleme izleme, izleme bir üretim ortamında performansı üzerinde en az etkiyle açılabilir. Bu izlemeler olayları ETW oturumuna olarak gösterilen.  
  
 Bu örnek, olayları Olay Görüntüleyicisi kullanılarak görüntülenebilir olay günlüğü için hizmetinden yayılan temel bir WCF hizmeti içerir. WCF hizmetinden gelen olayları dinler adanmış bir ETW oturumu başlatmak mümkündür. Örnek olayları Olay Görüntüleyicisi'ni kullanarak okunabilir ikili bir dosyada depolar adanmış bir ETW oturum oluşturmak için bir komut dosyası içerir.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], EtwAnalyticTraceSample.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Çözümü çalıştırmak için CTRL + F5 tuşuna basın.  
  
     Web tarayıcısında tıklatın **Calculator.svc**. Hizmet için WSDL belgenin URI tarayıcıda görüntülenmesi gerekir. Bu URI kopyalayın.  
  
     Varsayılan olarak, hizmet başlatır bağlantı 1378 isteklerini dinleme (http://localhost:1378/Calculator.svc).  
  
4.  WCF test istemcisi (WcfTestClient.exe) çalıştırın.  
  
     WCF test istemcisi (WcfTestClient.exe) bulunan \< [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] yükleme dizini > \Common7\IDE\ WcfTestClient.exe (varsayılan [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] yükleme dizini olan C:\Program Files\Microsoft Visual Studio 10.0).  
  
5.  WCF test istemcisi içinde hizmet seçerek eklemek **dosya**ve ardından **Hizmet Ekle**.  
  
     Uç nokta adresi giriş kutusuna ekleyin. Varsayılan, http://localhost:1378/Calculator.svc değeridir.  
  
6.  Olay Görüntüleyicisi'ni uygulamasını açın.  
  
     Hizmet çağrılırken önce Olay Görüntüleyicisi'ni başlatın ve WCF hizmetinden gösterilen olayları izlemek için olay günlüğüne dinlediğinden emin olun.  
  
7.  Gelen **Başlat** menüsünde, select **Yönetimsel Araçlar**ve ardından **Olay Görüntüleyicisi'ni**.  Etkinleştirme **analitik** ve **hata ayıklama** günlükleri.  
  
8.  Olay Görüntüleyicisi'nde ağaç görünümünde gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**ve ardından **Uygulama uygulamalarının**. Sağ **uygulama uygulamalarının**seçin **Görünüm**ve ardından **Analitik ve hata ayıklama günlüklerini göster**.  
  
     Emin **Analitik ve hata ayıklama günlüklerini göster** seçeneği denetlenir.  
  
9. Etkinleştirme **analitik** günlük.  
  
     Olay Görüntüleyicisi'nde ağaç görünümünde gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**ve ardından **Uygulama uygulamalarının**. Sağ **analitik** seçip **günlüğü etkinleştir**.  
  
#### <a name="to-test-the-service"></a>Hizmeti sınamak için  
  
1.  Çift tıklayın ve geçiş WCF test istemcisi geri `Divide` ve Payda 0 belirtin varsayılan değerleri koruyun.  
  
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
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric izleme örnekleri](http://go.microsoft.com/fwlink/?LinkId=193959)
