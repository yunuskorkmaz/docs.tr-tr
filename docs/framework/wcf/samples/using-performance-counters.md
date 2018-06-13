---
title: Performans Sayaçlarını Kullanma
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 8784b4a481b8313d370aad1d8f265dcb44ab3ed6
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807325"
---
# <a name="using-performance-counters"></a>Performans Sayaçlarını Kullanma
Bu örnek, Windows Communication Foundation (WCF) performans sayaçları erişmek nasıl ve kullanıcı tanımlı performans sayaçları oluşturma gösterilir. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Bu örnekte, istemci dört yöntemlerini çağıran `ICalculator` hizmet. İstemci kullanıcı tarafından kesilene kadar bunun devam eder. Hizmet değişmeden kalır.  
  
 Performans sayaçları hizmet için Web.config dosyasının tanılama bölümünde şu örnek yapılandırmada gösterildiği gibi etkinleştirilir.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />   
  </system.serviceModel>  
</configuration>  
```  
  
 Bu görev ayrıca yapılabilir kullanarak [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Performans sayaçları etkin olduğunda, tüm paketi WCF performans sayaçları için hizmet etkinleştirilir. .NET Framework, üç düzeyde performans verilerini otomatik olarak bulundurur: `ServiceModelService`, `ServiceModelEndpoint` ve `ServiceModelOperation`. Bu düzeylerin her birinde, performans sayaçları "Çağrıları", "Çağrıları saniyede" ve "Güvenlik çağrıları yetkilendirilmedi" gibi sahiptir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-view-performance-data"></a>Performans verilerini görüntülemek için  
  
1.  Performans İzleyicisi aracıyla tıklayarak Başlat **Başlat**, **Çalıştır...** , girin `perfmon` tıklatıp **Tamam** veya Denetim Masası'ndan seçin **Yönetimsel Araçlar** çift tıklayın ve **performans**.  
  
    > [!NOTE]
    >  Örnek kod çalışıncaya kadar sayaçları ekleyemezsiniz.  
  
2.  Bunları seçerek ve Delete tuşuna basarak listelenen performans sayaçlarını kaldırın.  
  
3.  WCF sayaçları Grafik bölmesi sağ tıklayıp seçerek eklemek **Sayaç Ekle**. İçinde **Sayaç Ekle** iletişim kutusunda **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0 veya ServiceModelService 3.0.0.0** performans nesnesi açılır liste kutusu. Listeden görüntülemek istediğiniz sayaçları seçin.  
  
    > [!NOTE]
    >  Bilgisayarda çalışan hiçbir WCF hizmetleri varsa bir hizmet için hiçbir WCF performans sayaçları vardır.  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a>Sayaçları etkinleştirmek için yapılandırma Düzenleyicisi'ni kullanmak için  
  
1.  SvcConfigEditor.exe örneği açın.  
  
2.  Dosya menüsünde **açık** ve ardından **yapılandırma dosyası...** .  
  
3.  Örnek uygulama hizmeti klasörüne gidin ve Web.config dosyasını açın.  
  
4.  Tıklatın **tanılama** yapılandırma ağaç.  
  
5.  İki durumlu **performans sayacı** içinde **tanılama** 'All' göstermek için penceresi.  
  
6.  Yapılandırma dosyasını kaydedin ve düzenleyiciden çıkın.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric izleme örnekleri](http://go.microsoft.com/fwlink/?LinkId=193959)
