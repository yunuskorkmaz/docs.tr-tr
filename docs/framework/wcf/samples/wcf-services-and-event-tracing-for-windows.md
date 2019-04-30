---
title: Windows için WCF Hizmetleri ve Etkinlik İzleme
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: 35d0202a3b9cf4060240dc521554644d419a5c23
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723179"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a>Windows için WCF Hizmetleri ve Etkinlik İzleme
Bu örnek, çözümleme izleme Windows Communication Foundation (WCF), olay izleme için Windows (ETW) olayları yaymak için nasıl kullanılacağını gösterir. Analitik izlemeleri, WCF hizmetleri üretim ortamında giderme sağlayan anahtar WCF yığın noktalarında yayılan olaylardır.

 WCF hizmetlerinde analitik izleme, izleme performans üzerinde en az etki ile bir üretim ortamında açılabilir. Bu izlemeler, olaylar bir ETW oturumu için olarak gönderilir.

 Bu örnek, olayları Olay Görüntüleyicisi kullanılarak görüntülenebilir olay günlüğü için hizmetten gönderilir, temel bir WCF hizmeti içerir. WCF hizmetinden gelen olayları dinler adanmış bir ETW oturumu başlatmak mümkündür. Örnek, olayları Olay Görüntüleyicisi'ni kullanarak okunabilir ikili bir dosyada depolayan ayrılmış bir ETW oturumu oluşturmak için bir betik içerir.

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2012 kullanarak EtwAnalyticTraceSample.sln çözüm dosyasını açın.

2. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.

3. Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.

     Web tarayıcısında tıklayın **Calculator.svc**. WSDL belgesinde hizmet URI'si tarayıcı içinde görüntülenmesi gerekir. Bu URI'yi kopyalayın.

     Varsayılan olarak, hizmet başlatılır 1378 bağlantı noktası isteklerini dinlemeye `http://localhost:1378/Calculator.svc`.

4. WCF test istemcisi (WcfTestClient.exe) çalıştırın.

     WCF test istemcisi (WcfTestClient.exe) şu konumdadır `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.  Varsayılan Visual Studio 2012 yükleme dizini olan `C:\Program Files\Microsoft Visual Studio 10.0`.

5. WCF test istemcisi içinde hizmet seçerek ekleyin **dosya**, ardından **Hizmet Ekle**.

     Uç nokta adresi giriş kutusuna ekleyin. Varsayılan, `http://localhost:1378/Calculator.svc` değeridir.

6. Olay Görüntüleyici uygulamasını açın.

     Hizmetini çağırmak önce Olay Görüntüleyicisi'ni başlatın ve olay günlüğüne olayları WCF hizmetinden yayılan izleme dinlediğinden emin olun.

7. Gelen **Başlat** menüsünde **Yönetimsel Araçlar**, ardından **Olay Görüntüleyicisi'ni**.  Etkinleştirme **analitik** ve **hata ayıklama** günlükleri.

8. Olay Görüntüleyicisi'nde ağaç görünümünde gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**ve ardından **Uygulama uygulamalarının**. Sağ **uygulama uygulamalarının**seçin **görünümü**, ardından **Analitik ve hata ayıklama günlüklerini göster**.

     Emin **Analitik ve hata ayıklama günlüklerini göster** seçeneği denetlenir.

9. Etkinleştirme **analitik** günlük.

     Olay Görüntüleyicisi'nde ağaç görünümünde gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**ve ardından **Uygulama uygulamalarının**. Sağ **analitik** seçip **günlüğü etkinleştir**.

#### <a name="to-test-the-service"></a>Hizmeti test etmek için

1. WCF test istemcisi geri geçiş yapmak ve çift `Divide` ve bir Payda 0 belirtin varsayılan değerleri koruyun.

     Payda 0 ise, hizmet bir hata oluşturur.

2. Hizmetten yayılan olayları gözlemektir.

     Olay Görüntüleyicisi'ne geçin ve gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**ve ardından **Uygulama uygulamalarının**. Sağ **analitik** seçip **Yenile**.

     WCF analiz izleme olayları Olay Görüntüleyicisi'nde görüntülenir. Tarafından bir hata oluştuğundan bir hata izleme olayı service Olay Görüntüleyicisi görüntülenen dikkat edin.

3. 1 ve 2, ancak geçerli girişler. Değerini `N2` parametresi 0 dışındaki herhangi bir sayı olabilir.

     WCF görüntülemek için analitik kanal Yenile olayları hata olaylarını dahil değildir.

 Örnek, bir WCF hizmetinden yayılan analitik izleme olayları gösterir.

#### <a name="to-cleanup-optional"></a>(İsteğe bağlı) temizlemek için

1. Olay Görüntüleyicisi'ni açın.

2. Gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, ardından  **Uygulama sunucusu uygulamalar**. Sağ **analitik** seçip **devre dışı günlük**.

3. Gidin **Olay Görüntüleyicisi'ni**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**, ardından  **Uygulama sunucusu uygulamalar**. Sağ **analitik** seçip **Günlüğü Temizle**.

4. Seçin **Temizle** olayları silmek için seçeneği.

> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric izleme örnekleri](https://go.microsoft.com/fwlink/?LinkId=193959)
