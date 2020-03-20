---
title: Performans Sayaçlarını Kullanma
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 7ffd9f5de5efb4be22968958246839e804daf23d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143583"
---
# <a name="using-performance-counters"></a>Performans Sayaçlarını Kullanma
Bu örnek, Windows Communication Foundation (WCF) performans sayaçlarına nasıl erişilmeyi ve kullanıcı tanımlı performans sayaçlarının nasıl oluşturulacaklarını göstermektedir. Bu örnek [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)dayanmaktadır.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Bu örnekte, istemci hizmetin dört `ICalculator` yöntemini çağırır. İstemci, kullanıcı tarafından kesintiye uğrayana kadar bunu yapmaya devam ediyor. Hizmet değişmeden kalır.  
  
 Performans sayaçları, aşağıdaki örnek yapılandırmada gösterildiği gibi, hizmet için Web.config dosyasının tanılama bölümünde etkinleştirilir.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />
  </system.serviceModel>  
</configuration>  
```  
  
 Bu görev configuration editor [aracı (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)kullanılarak da yapılabilir.  
  
 Performans sayaçları etkinleştirildiğinde, hizmet için WCF performans sayaçlarının tamamı etkinleştirilir. .NET Framework, performans verilerini otomatik olarak `ServiceModelService`üç `ServiceModelEndpoint` `ServiceModelOperation`düzeyde tutar: ve . Bu düzeylerin her birinde "Aramalar", "Saniyebaşına Aramalar" ve "Yetkili Olmayan Güvenlik Çağrıları" gibi performans sayaçları bulunur.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya bilgisayar lar arası yapılandırmada çalıştırmak [için, Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
### <a name="to-view-performance-data"></a>Performans verilerini görüntülemek için  
  
1. Performans İzleme Aracını **Başlat,** **Çalıştır...** seçeneğini `perfmon` tıklatarak başlatın, **Tamam'a** girin ve tıklayın veya Denetim Masası'ndan **Yönetim Araçları'nı** seçin ve **Performans'ı**çift tıklatın.  
  
    > [!NOTE]
    > Örnek kod çalışmayana kadar sayaç ekleyemezsiniz.  
  
2. Bunları seçerek ve Sil tuşuna basarak listelenen performans sayaçlarını kaldırın.  
  
3. Grafik bölmesine sağ tıklayarak ve Sayaç Ekle'yi seçerek WCF **sayaçları**ekleyin. Sayaç **Ekle** iletişim kutusunda, **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0 veya ServiceModelService 3.0.0.0.0'ı** Seç nesnesi açılan liste kutusunda seçin. Listeden görüntülemek istediğiniz sayaçları seçin.  
  
    > [!NOTE]
    > Bilgisayarda çalışan WCF hizmetleri yoksa, bir hizmet için WCF performans sayacı yoktur.  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a>Sayaçları etkinleştirmek için Configuration Editor'u kullanmak için  
  
1. SvcConfigEditor.exe bir örnek açın.  
  
2. Dosya menüsünde **Aç'ı** tıklatın ve **ardından Config dosyasını tıklatın...**.  
  
3. Örnek uygulamanın hizmet klasörüne gidin ve Web.config dosyasını açın.  
  
4. Yapılandırma ağacında **Tanılama'yı** tıklatın.  
  
5. 'Tümü'nu göstermek için **Tanılama** penceresinde **Performans Sayacını** titretin.  
  
6. Yapılandırma dosyasını kaydedin ve düzenleyiciden çıkın.  
  
> [!IMPORTANT]
> Örnekler bilgisayarınıza zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric İzleme Örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
