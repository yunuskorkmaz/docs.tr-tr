---
title: "Dinamik Yeniden Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b20786ae-cce6-4f91-b6cb-9cae116faf8b
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3146da86dcbe22f72ebedec57c87ac0a29ed1946
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="dynamic-reconfiguration"></a>Dinamik Yeniden Yapılandırma
Bu örnek gösterilmektedir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] yönlendirme hizmeti. Yönlendirme hizmeti bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] içerik tabanlı yönlendirici uygulamanıza dahil kolaylaştırır bileşeni. Bu örnek standart uyum [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hesaplayıcı yönlendirme hizmeti kullanarak iletişim kurmak için örnek. Bu örnek nasıl yönlendirme hizmeti dinamik olarak çalışma zamanı sırasında yeniden yapılandırılabilen gösterir.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\DynamicReconfiguration`  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Yönlendirme hizmeti çalışma zamanı sırasında dinamik olarak yapılandırmak için bu örnek yeni bir oluşturur beş saniyede bir süreölçer harekete <xref:System.ServiceModel.Routing.RoutingConfiguration> nesne ve uygular. Bu yapılandırma, normal hesaplayıcı uç nokta veya yuvarlama hesaplayıcı endpoint başvurur. Bir hizmeti veya diğer, yönlendirme hizmeti hangisinin bağlı olarak yapılandırılmış döndürülen kendi iletileri hesaplayıcı istemci uygulaması olan o zaman için rota.  
  
 Yönlendirme hizmetin capabilitiy özel bir davranış aracılığıyla dinamik yeniden yapılandırılması için kullanılır. Bu özel davranışı için bir geri çağırma edilir beş saniyede tetiklenen basit iş parçacığı süreölçer içeren bir hizmet uzantısı ekler `UpdateRules` yöntemi. Bu geri çağırma oluşturur ve yeni yönlendirme yapılandırması uygular. Gerçek bir dağıtımda bulunan bu geri çağırma sonucunda başka türden bir olay, bir SQL olay bildirim ya da bir WS-bulma Duyurusu gibi büyük olasılıkla gerçekleştirilmesi.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], DynamicReconfiguration.sln açın.  
  
2.  Açmak için **Çözüm Gezgini**seçin **Çözüm Gezgini** gelen **Görünüm** menüsü.  
  
3.  Tuşuna **F5** veya **CTRL + SHIFT + B** içinde [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].  
  
    1.  Otomatik gerekli projeleri bastığınızda başlatılan isteyip **F5**, çözüme sağ tıklayın ve seçin **özellikleri**. Seçin **başlangıç projesi** düğümü altında **ortak özellikleri** sol bölmede. Seçin **birden fazla başlangıç projesi** radyo düğmesinin ve tüm projeleri için ayarlanmış **Başlat** eylem.  
  
    2.  Proje ile yapı **CTRL + SHIFT + B**, aşağıdaki uygulamalar başlatmanız gerekir:  
  
        1.  Hesaplayıcı istemci (. / CalculatorClient/bin/client.exe)  
  
        2.  Hesap Makinesi hizmetinin (. / CalculatorService/bin/service.exe)  
  
        3.  Yönlendirme hesap makinesi hizmetinin (. / RoundingCalcService/bin/service.exe)  
  
        4.  RoutingService (. / RoutingService/bin/RoutingService.exe)  
  
4.  Hesaplayıcı istemci konsol penceresinde istemci başlatmak ve hesaplayıcı hizmet işlemlerini çağırma için ENTER tuşuna basın.  
  
     Yönlendirme hizmeti iletileri yuvarlama hesaplayıcı ve normal hesaplayıcı dönüşümlü yönlendirme yapılandırması değişiklikleri dinamik olarak beş saniyede yönlendirir. Yönlendirme hizmeti ileti göndermek için yapılandırılan hangi uç noktası bağlı olarak farklı çıkışları istemci konsol penceresinde vardır.  
  
5.  Sürekli olarak beş saniyeden fazla ENTER tuşuna basarak devam ve hizmet sonuçlarından değişikliği gözlemleyin.  
  
    1.  Yönlendirici hizmeti yuvarlama hesaplayıcı hizmetine iletileri yönlendirmek üzere yapılandırılırsa çıkış döndürülen verilmiştir.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.2  
        Divide(22,7) = 3.1  
        ```  
  
    2.  Yönlendirme hizmeti normal hesaplayıcı hizmetine iletileri yönlendirmek üzere yapılandırılırsa çıkış döndürülen verilmiştir.  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
6.  Hesaplayıcı hizmeti ve yuvarlama hesaplayıcı hizmeti ilgili konsol pencerelerini çağrılan işlemlerinin bir günlük çıkışı da yazdırın.  
  
7.  İstemci konsol penceresinde "Çık" yazın ve ENTER tuşuna basarak çıkın.  
  
8.  Hizmetler konsolunda Windows Hizmetleri sonlandırmak için ENTER tuşuna basın.  
  
## <a name="scenario"></a>Senaryo  
 Bu örnek, birden çok türleri veya hizmetleri uygulaması bir uç noktası aracılığıyla açığa çıkarılması izin vererek içerik tabanlı bir yönlendirici işlevi gören yönlendirici gösterir.  
  
### <a name="real-world-scenario"></a>Gerçek dünya senaryosu  
 Contoso tüm genel olarak, bunlar birden çok farklı türlerdeki Hizmetleri için erişim sunar tek bir uç nokta kullanıma sunmak için kendi Hizmetleri sanallaştırmayı istiyor. Bu durumda, gelen isteklerin gönderilmesi gerektiğini belirlemek için yönlendirme hizmetin içerik tabanlı Yönlendirme yetenekleri kullanın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric barındırma ve kalıcılığı örnekleri](http://go.microsoft.com/fwlink/?LinkId=193961)
