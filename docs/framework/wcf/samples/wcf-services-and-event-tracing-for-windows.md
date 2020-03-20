---
title: Windows için WCF Hizmetleri ve Etkinlik İzleme
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: b8a1f30f20aa2c541a574a070b3644569d633ca2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183207"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a>Windows için WCF Hizmetleri ve Etkinlik İzleme
Bu örnek, Windows İletişim Vakfı'ndaki (WCF) analitik izlemenin, Windows için Olay İzleme (ETW) etkinliklerini yalamak için nasıl kullanılacağını göstermektedir. Analitik izlemeler, WCF yığınının kilit noktalarında yayılan ve WCF hizmetlerinin üretim ortamında sorun gidermesine olanak tanıyan olaylardır.

 WCF hizmetlerinde analitik izleme, performans üzerinde en az etkiye sahip bir üretim ortamında açılabilir izleme. Bu izlemeler bir ETW oturumuna olay olarak yayılır.

 Bu örnek, olayların hizmetten olay günlüğüne yayıldığı ve Olay Görüntüleyicisi kullanılarak görüntülenebilen temel bir WCF hizmetini içerir. Ayrıca, WCF hizmetindeki etkinlikleri dinleyen özel bir ETW oturumu başlatmak da mümkündür. Örnek, olayları Olay Görüntüleyicisi kullanılarak okunabilen ikili bir dosyada depolayan özel bir ETW oturumu oluşturmak için bir komut dosyası içerir.

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2012'yi kullanarak EtwAnalyticTraceSample.sln çözüm dosyasını açın.

2. Çözümü oluşturmak için CTRL+SHIFT+B tuşuna basın.

3. Çözümü çalıştırmak için CTRL+F5 tuşuna basın.

     Web tarayıcısında, **Calculator.svc'yi**tıklatın. Hizmet için WSDL belgesinin URI tarayıcıda görünmelidir. Uri'yi kopyala.

     Varsayılan olarak, hizmet bağlantı noktası 1378 `http://localhost:1378/Calculator.svc`isteklerini dinlemeye başlar.

4. WCF test istemcisini çalıştırın (WcfTestClient.exe).

     WCF test istemcisi (WcfTestClient.exe) `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`adresinde yer alır.  Varsayılan Visual Studio 2012 `C:\Program Files\Microsoft Visual Studio 10.0`yüklemek dir .

5. WCF test istemcisi içinde, **Dosya**seçerek hizmet ekleyin ve sonra **Hizmet ekle**.

     Giriş kutusuna bitiş noktası adresini ekleyin. Varsayılan değer: `http://localhost:1378/Calculator.svc`.

6. Olay Görüntüleyicisi uygulamasını açın.

     Hizmeti başlatmadan önce Olay Görüntüleyicisi'ni başlatın ve olay günlüğünün WCF hizmetinden yayılan olayları izlemek için dinlediğinden emin olun.

7. **Başlat** menüsünden **Yönetim Araçları'nı**ve ardından **Olay Görüntüleyicisi'ni**seçin.  **Analitik** ve **Hata Ayıklama** günlüklerini etkinleştirin.

8. Olay Görüntüleyici'deki ağaç görünümünde, **Olay Görüntüleyicisi,** **Uygulamalar ve Hizmetler Günlükleri,** **Microsoft,** **Windows**ve ardından **Uygulama Sunucusu-Uygulamaları'na**gidin. **Uygulama Sunucusu Uygulamaları'nı**sağ tıklatın, **Görünüm'i**seçin ve ardından Analitik ve **Hata Ayıklama Günlüklerini Göster'i**seçin.

     **Analitik ve Hata Ayıklama Günlükleri'ni göster** seçeneğinin işaretli olduğundan emin olun.

9. **Analitik** günlüğünü etkinleştirin.

     Olay Görüntüleyici'deki ağaç görünümünde, **Olay Görüntüleyicisi,** **Uygulamalar ve Hizmetler Günlükleri,** **Microsoft,** **Windows**ve ardından **Uygulama Sunucusu-Uygulamaları'na**gidin. **Analytic'e** sağ tıklayın ve **Günlüğü Etkinleştir'i**seçin.

#### <a name="to-test-the-service"></a>Hizmeti test etmek için

1. WCF test istemcisine geri dön `Divide` ve çift tıklatın ve 0 paydasını belirten varsayılan değerleri koruyun.

     Payda 0 ise, servis bir hata atar.

2. Hizmetten yayılan olayları gözlemleyin.

     Olay Görüntüleyici'ye geri dön ve **Olay Görüntüleyicisi,** **Uygulamalar ve Hizmetler Günlükleri,** **Microsoft,** **Windows**ve ardından **Uygulama Sunucusu-Uygulamaları'na**gidin. **Analytic'e** sağ tıklayın ve **Yenile'yi**seçin.

     WCF analitik izleme olayları olay görüntüleyicisinde görüntülenir. Hizmet tarafından bir hata atıldığı için olay görüntüleyicisinde bir hata izleme olayının görüntülendiğine dikkat edin.

3. 1 ve 2 adımlarını, ancak geçerli girişlerle yineleyin. Parametrenin `N2` değeri 0'dan başka herhangi bir sayı olabilir.

     WCF olaylarını görüntülemek için analitik kanalı yenileyin herhangi bir hata olayı içermez.

 Örnek, bir WCF hizmetinden yayılan analitik izleme olaylarını gösterir.

#### <a name="to-cleanup-optional"></a>Temizlemek için (İsteğe Bağlı)

1. Olay Görüntüleyicisi'ni açın.

2. Olay **Görüntüleyici,** **Uygulamalar ve Hizmetler Günlükleri,** **Microsoft,** **Windows**ve ardından **Uygulama-Sunucu Uygulamaları**gidin. **Analytic'e** sağ tıklayın ve **Günlük'ünü Devre Dışı Nı**seçin.

3. Olay **Görüntüleyici,** **Uygulamalar ve Hizmetler Günlükleri,** **Microsoft,** **Windows**ve ardından **Uygulama-Sunucu Uygulamaları**gidin. **Analytic'e** sağ tıklayın ve **Günlük'u temizle'yi**seçin.

4. Olayları temizlemek için **Temizle** seçeneğini belirleyin.

> [!IMPORTANT]
> Örnekler bilgisayarınıza zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric İzleme Örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
