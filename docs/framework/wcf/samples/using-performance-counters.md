---
title: Performans Sayaçlarını Kullanma
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 787a3d08b463980721fb207d029057e14618db5e
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43860425"
---
# <a name="using-performance-counters"></a>Performans Sayaçlarını Kullanma
Bu örnek, kullanıcı tanımlı performans Sayaçlarınızı oluşturma işlemleri ve Windows Communication Foundation (WCF) performans sayaçlarını nasıl gösterir. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Bu örnekte, dört yöntemlerinin istemci çağrıları `ICalculator` hizmeti. İstemci, kullanıcı tarafından kesintiye kadar devam eder. Hizmet değişmeden kalır.  
  
 Performans sayaçları hizmeti için Web.config dosyasının tanılama bölümünde şu örnek yapılandırmada gösterildiği etkinleştirilir.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />   
  </system.serviceModel>  
</configuration>  
```  
  
 Bu görevi de yapılabilir kullanarak [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Performans sayaçlarını etkin olduğunda, tüm WCF performans sayaçları dizisi için hizmet etkinleştirilir. .NET Framework, üç düzeyde performans verilerini otomatik olarak bulundurur: `ServiceModelService`, `ServiceModelEndpoint` ve `ServiceModelOperation`. Bu düzeylerinin her biri "Çağrıları", "Çağrıları saniye başına" ve "Güvenlik çağrıları yetkilendirilmedi" gibi performans sayaçları sahiptir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-view-performance-data"></a>Performans verilerini görüntülemek için  
  
1.  Tıklayarak Performans İzleyicisi Aracı'nı başlatın **Başlat**, **Çalıştır...** , girin `perfmon` tıklatıp **Tamam** veya Denetim Masası'ndan seçin **Yönetimsel Araçlar** ve çift **performans**.  
  
    > [!NOTE]
    >  Örnek kodunu çalıştıran dek sayaçları ekleyemezsiniz.  
  
2.  Bunları seçerek ve Delete tuşuna basarak listelenen performans sayaçlarını kaldırın.  
  
3.  Grafik bölmesi sağ tıklatıp seçerek WCF sayaçları ekleyin **Sayaç Ekle**. İçinde **Sayaç Ekle** iletişim kutusunda **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0 veya ServiceModelService 3.0.0.0** performans nesnesinde açılan liste kutusu. Listeden görüntülemek istediğiniz sayaçları seçin.  
  
    > [!NOTE]
    >  Bilgisayarda çalışan bir WCF Hizmeti yok ise hiçbir WCF performans sayaçları için bir hizmet vardır.  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a>Sayaçları etkinleştirmek için yapılandırma Düzenleyicisi'ni kullanmak için  
  
1.  SvcConfigEditor.exe örneği açın.  
  
2.  Dosya menüsünde **açık** ve ardından **yapılandırma dosyası...** .  
  
3.  Örnek uygulama hizmeti klasörüne gidin ve Web.config dosyasını açın.  
  
4.  Tıklayın **tanılama** yapılandırma ağaç.  
  
5.  İki durumlu **performans sayacı** içinde **tanılama** 'All' gösterilecek penceresi.  
  
6.  Yapılandırma dosyasını kaydedin ve düzenleyiciden çıkın.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric izleme örnekleri](https://go.microsoft.com/fwlink/?LinkId=193959)
