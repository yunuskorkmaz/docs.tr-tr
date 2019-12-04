---
title: Windows için WCF Hizmetleri ve Etkinlik İzleme
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: 93663cbc33b6fab9b34bb02187e5b04192f5c13d
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715259"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a>Windows için WCF Hizmetleri ve Etkinlik İzleme
Bu örnek, Windows için olay Izleme (ETW) içindeki olayları göstermek için Windows Communication Foundation (WCF) ' de analitik izlemenin nasıl kullanılacağını gösterir. Analitik izlemeler, WCF yığınında, üretim ortamındaki WCF hizmetlerinde sorun gidermeye izin veren önemli noktalara yayılan olaylardır.

 WCF Hizmetlerinde analitik izleme, performans üzerinde en az etkisi olan bir üretim ortamında açılıp açılbiliyordu. Bu izlemeler bir ETW oturumuna olay olarak dağıtılır.

 Bu örnek, olayların hizmetten, Olay Görüntüleyicisi kullanılarak görüntülenebilen olay günlüğüne oluşturulduğu temel bir WCF hizmeti içerir. WCF hizmetinden olayları dinleyen özel bir ETW oturumu başlatmak da mümkündür. Örnek, Olay Görüntüleyicisi kullanılarak okunabilen bir ikili dosyada olayları depolayan adanmış bir ETW oturumu oluşturmak için bir komut dosyası içerir.

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2012 kullanarak, Etwanaltictracesample. sln çözüm dosyasını açın.

2. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.

3. Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.

     Web tarayıcısında, **Hesaplayıcı. svc**' ye tıklayın. Hizmet için WSDL belgesinin URI 'SI tarayıcıda görünmelidir. Bu URI 'yi kopyalayın.

     Hizmet, varsayılan olarak 1378 numaralı bağlantı noktasında istekleri dinlemeye başlar `http://localhost:1378/Calculator.svc`.

4. WCF test istemcisini (WcfTestClient. exe) çalıştırın.

     WCF Test istemcisi (WcfTestClient. exe) `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`konumunda bulunur.  Varsayılan Visual Studio 2012 Install dir `C:\Program Files\Microsoft Visual Studio 10.0`.

5. WCF Test istemcisi içinde **Dosya**' yı ve ardından **Hizmet Ekle**' yi seçerek hizmeti ekleyin.

     Giriş kutusuna uç nokta adresini ekleyin. Varsayılan, `http://localhost:1378/Calculator.svc` değeridir.

6. Olay Görüntüleyicisi uygulamasını açın.

     Hizmeti çağırmadan önce Olay Görüntüleyicisi başlatın ve olay günlüğünün WCF hizmetinden yayılan izleme olaylarını dinlediğinden emin olun.

7. **Başlat** menüsünde, **Yönetim Araçları**' nı seçin ve ardından **Olay Görüntüleyicisi**.  **Analitik** ve **hata ayıklama** günlüklerini etkinleştirin.

8. Olay Görüntüleyicisi ' deki ağaç görünümünde **Olay Görüntüleyicisi**, **uygulamalar ve hizmetler günlükleri**, **Microsoft**, **Windows**ve ardından **uygulama sunucusu-uygulamalar**' a gidin. **Uygulama sunucusu-uygulamalar**' a sağ tıklayın, **Görünüm**' ü seçin ve ardından **analitik ve hata ayıklama günlüklerini görüntüleyin**.

     **Analitik ve hata ayıklama günlüklerini göster** seçeneğinin işaretli olduğundan emin olun.

9. **Analitik** günlüğü etkinleştirin.

     Olay Görüntüleyicisi ' deki ağaç görünümünde **Olay Görüntüleyicisi**, **uygulamalar ve hizmetler günlükleri**, **Microsoft**, **Windows**ve ardından **uygulama sunucusu-uygulamalar**' a gidin. **Analitik** öğesine sağ tıklayın ve **günlüğü etkinleştir**' i seçin.

#### <a name="to-test-the-service"></a>Hizmeti test etmek için

1. WCF test istemcisine geri dönün ve `Divide` çift tıklayın ve 0 paydasını belirten varsayılan değerleri tutun.

     Payda 0 ise, hizmet bir hata oluşturur.

2. Hizmetten yayılan olayları gözlemleyin.

     Olay Görüntüleyicisi dönün ve **Olay Görüntüleyicisi**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**ve **uygulama sunucusu-uygulamalar**' a gidin. **Analitik** ' e sağ tıklayın ve **Yenile**' yi seçin.

     WCF analitik izleme olayları Olay Görüntüleyicisi 'nde görüntülenir. Olay görüntüleyicisindeki bir hata izleme olayı tarafından bir hata oluşturulduğuna dikkat edin.

3. 1 ve 2. adımları, ancak geçerli girişlerle tekrarlayın. `N2` parametresinin değeri 0 dışında herhangi bir sayı olabilir.

     WCF olaylarını görüntülemek için analitik kanalı yenileme herhangi bir hata olayı içermez.

 Örnek, bir WCF hizmetinden yayılan analitik izleme olaylarını gösterir.

#### <a name="to-cleanup-optional"></a>Temizlemek için (Isteğe bağlı)

1. Olay Görüntüleyicisi'ni açın.

2. **Olay Görüntüleyicisi**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**ve sonra **uygulama-sunucu uygulamaları**' na gidin. **Analitik** öğesine sağ tıklayın ve **günlüğü devre dışı bırak**' ı seçin.

3. **Olay Görüntüleyicisi**, **uygulama ve hizmet günlükleri**, **Microsoft**, **Windows**ve sonra **uygulama-sunucu uygulamaları**' na gidin. **Analitik** öğesine sağ tıklayın ve **Günlüğü Temizle**' yi seçin.

4. Olayları temizlemek için **Temizle** seçeneğini belirleyin.

> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric Izleme örnekleri](https://go.microsoft.com/fwlink/?LinkId=193959)
