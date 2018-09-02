---
title: Dinamik Yeniden Yapılandırma
ms.date: 03/30/2017
ms.assetid: b20786ae-cce6-4f91-b6cb-9cae116faf8b
ms.openlocfilehash: a147a1d6cf61001832661376363ecc850ecad309
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401346"
---
# <a name="dynamic-reconfiguration"></a>Dinamik Yeniden Yapılandırma
Bu örnek, Windows Communication Foundation (WCF) yönlendirme hizmeti gösterir. Yönlendirme hizmeti, içerik tabanlı bir yönlendirici uygulamanıza dahil etmek kolay bir WCF bileşenidir. Bu örnek, yönlendirme hizmeti kullanarak iletişim kurmak için standart WCF hesaplayıcı örnek uyum sağlar. Bu örnek nasıl yönlendirme hizmeti dinamik olarak çalışma zamanı sırasında yapılandırılabilen gösterir.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\DynamicReconfiguration`  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Yönlendirme hizmeti çalışma zamanı sırasında dinamik olarak yeniden yapılandırmak için bu örnek yeni bir oluşturur her beş saniyede bir zamanlayıcı harekete <xref:System.ServiceModel.Routing.RoutingConfiguration> nesne ve uygular. Bu yapılandırma, normal hesaplayıcı uç nokta veya yuvarlama hesaplayıcı uç nokta başvuruyor. Hesaplayıcı istemci uygulaması sahip bir hizmet veya diğer, yönlendirme hizmeti hangisinin bağlı olarak yapılandırılmış döndürülen iletileri yönlendirmek için o zaman.  
  
 Yönlendirme hizmetin capabilitiy dinamik yeniden yapılandırma yoluyla özel bir davranış için kullanılır. Bu özel davranışı için bir geri çağırma sonuçlanır her beş saniyede tetiklenen basit bir iş parçacığı Zamanlayıcı içeren bir hizmet uzantısı ekler `UpdateRules` yöntemi. Bu geri çağırma oluşturur ve bu yeni yönlendirme yapılandırması uygular. Gerçek bir dağıtımda, bu geri çağırma büyük olasılıkla başka türde bir SQL olay bildirimi ya da bir WS-bulma Duyurusu gibi bir olay sonucunda ulaşılacağına.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], DynamicReconfiguration.sln açın.  
  
2.  Açmak için **Çözüm Gezgini**seçin **Çözüm Gezgini** gelen **görünümü** menüsü.  
  
3.  Tuşuna **F5** veya **CTRL + SHIFT + B** Visual Studio'da.  
  
    1.  Bunu otomatik gerekli projeleri bastığınızda başlatma isterseniz **F5**, çözümü sağ tıklatın ve seçin **özellikleri**. Seçin **başlangıç projesi** düğümünde **ortak özellikler** sol bölmesinde. Seçin **birden fazla başlangıç projesi** radyo düğmesini ve tüm projeler için **Başlat** eylem.  
  
    2.  Projesiyle yapı **CTRL + SHIFT + B**, şu uygulamalar başlatmanız gerekir:  
  
        1.  Hesaplayıcı istemci (. / CalculatorClient/bin/client.exe)  
  
        2.  Hesaplayıcı hizmeti (. / CalculatorService/bin/service.exe)  
  
        3.  Yönlendirme hesaplayıcı hizmeti (. / RoundingCalcService/bin/service.exe)  
  
        4.  RoutingService (. / RoutingService/bin/RoutingService.exe)  
  
4.  Konsol penceresinde hesaplayıcı istemcinin, istemci başlatmak ve hesaplayıcı hizmet işlemlerini aramak için ENTER tuşuna basın.  
  
     Yönlendirme hizmeti iletileri yuvarlama hesaplayıcı ve normal hesaplayıcı için alternatif yönlendirme yapılandırma değişiklikleri dinamik olarak beş saniyede yönlendirir. Yönlendirme hizmeti, ileti göndermek için yapılandırılır hangi uç noktaya bağlı olarak farklı çıkış istemci konsol penceresinde vardır.  
  
5.  Sürekli olarak beş saniyeden fazla ENTER tuşuna basarak devam edin ve sonuçları hizmetinden değişiklik gözlemleyin.  
  
    1.  Yönlendirici hizmeti iletileri yuvarlama hesaplayıcı hizmetine yönlendirmek üzere yapılandırılmışsa çıkış döndürülen verilmiştir.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.2  
        Divide(22,7) = 3.1  
        ```  
  
    2.  Yönlendirme hizmeti iletileri normal hesaplayıcı hizmetine yönlendirmek üzere yapılandırılmışsa çıkış döndürülen verilmiştir.  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
6.  Hesaplayıcı hizmetini ve yuvarlama hesaplayıcı hizmetini de ilgili konsol pencerelerini çağrılan işlem günlüğünü dışarı yazdırın.  
  
7.  İstemci konsol penceresinde "Çık" yazın ve çıkmak için ENTER tuşuna basın.  
  
8.  Hizmetleri sonlandırmak için hizmetler Konsolu pencerelerinde ENTER tuşuna basın.  
  
## <a name="scenario"></a>Senaryo  
 Bu örnek, birden çok türleri veya uygulama hizmetleri bir uç nokta sağlamak ve içerik tabanlı bir yönlendirici görevi gören yönlendirici gösterir.  
  
### <a name="real-world-scenario"></a>Gerçek dünya senaryosu  
 Contoso tüm genel olarak, birden çok farklı türlerdeki Hizmetleri erişim sundukları tek bir uç nokta kullanıma sunmak için kendi hizmetlerini sanallaştırılması istemektedir. Bu durumda, gelen istekleri nereye gönderileceğini belirlemek için yönlendirme hizmetin içerik tabanlı yönlendirme becerilerinden.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric barındırma ve Kalıcılık örnekleri](https://go.microsoft.com/fwlink/?LinkId=193961)
