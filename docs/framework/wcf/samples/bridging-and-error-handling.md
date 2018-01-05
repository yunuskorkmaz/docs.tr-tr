---
title: "Köprü Oluşturma ve Hata İşleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ae87d1a-b615-4014-a494-a53f63ff0137
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 84a7d3385d89d4308e6a75d303a567fb4d7b22d3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="bridging-and-error-handling"></a>Köprü Oluşturma ve Hata İşleme
Bu örnek gösterilmektedir nasıl [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] yönlendirme hizmeti, bir istemci ile farklı bağlamaları kullanan bir hizmeti arasındaki iletişimi köprü oluşturma için kullanılır. Bu örnek ayrıca yedekleme Hizmeti'nin yük devretme senaryoları için nasıl kullanılacağını gösterir. Yönlendirme hizmeti bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] içerik tabanlı yönlendirici uygulamanıza dahil kolaylaştırır bileşeni. Bu örnek standart uyum [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hesaplayıcı yönlendirme hizmeti kullanarak iletişim kurmak için örnek.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\ErrorHandlingAndBridging`  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Bu örnekte, hesaplayıcı istemci yönlendirici tarafından kullanıma sunulan bir uç nokta ileti göndermek için yapılandırılır. Yönlendirme hizmeti, kendisine gönderilen tüm iletileri kabul etmek ve hesaplayıcı hizmeti karşılık gelen bir uç nokta iletmek için yapılandırılır. Aşağıdaki noktaları birincil hesaplayıcı hizmeti, yedekleme hesaplayıcı hizmet ve hesaplayıcı istemci ve istemci hizmeti arasındaki iletişimi nasıl gerçekleştiğini yapılandırmasını açıklamak yönlendirme hizmeti kullanarak:  
  
-   Hesaplayıcı istemci, hesap makinesi hizmetinin NetTcpBinding kullanacak şekilde yapılandırılırken BasicHttpBinding kullanmak üzere yapılandırılmış. İletileri gerektiğinde otomatik olarak dönüştürür hesaplayıcı hizmete göndermeden önce yönlendirme hizmeti ve hesaplayıcı istemci bunlara erişebilmesi için yanıtlar aynı zamanda dönüştürür.  
  
-   Yönlendirme hizmeti iki hesaplayıcı hizmetleri hakkında bilir: birincil hesaplayıcı hizmeti ve yedekleme hesaplayıcı hizmeti. Yönlendirme hizmeti, ilk birincil hesaplayıcı Hizmeti uç noktası ile iletişim kurmaya çalışır. Kapandıktan endpoint nedeniyle bu girişim başarısız olursa, yönlendirme hizmeti sonra yedekleme hesaplayıcı Hizmeti uç noktası ile iletişim kurmaya çalışır.  
  
 Bu nedenle istemci tarafından gönderilen iletileri yönlendirici tarafından alınır ve gerçek hesaplayıcı hizmete yönlendirilir. Hesaplayıcı hizmet uç noktası kapalı ise, yönlendirme hizmeti iletiyi yedekleme hesaplayıcı hizmet uç noktasına yönlendirir. Yedekleme hesaplayıcı hizmetinden gelen iletileri geri sırayla bunları hesaplayıcı istemciye aktarır hizmet yönlendiriciye gönderilir.  
  
> [!NOTE]
>  Yedekleme listesini tanımlanan birden fazla uç noktası olabilir. Bu durumda yedekleme Hizmeti uç noktası kapalı ise, yönlendirme hizmeti başarılı bir bağlantı gerçekleşene kadar sonraki yedekleme uç nokta listesinde bağlanmak çalışır.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], RouterBridgingAndErrorHandling.sln açın.  
  
2.  Visual Studio'da F5'e veya CTRL + SHIFT + B tuşuna basın  
  
    1.  Otomatik gerekli projeleri F5 tuşuna bastığınızda başlatılan almak istiyorsanız, çözüme sağ tıklayın, seçin **özellikleri**hem de **başlangıç projesi** düğümü altında **ortak özellikleri**seçin **birden fazla başlangıç projesi**, tüm projeleri ayarlanmış ve **Başlat**.  
  
    2.  CTRL + SHIFT + B projeyle oluşturuyorsanız, aşağıdaki uygulamalar başlatın:  
  
        1.  Hesaplayıcı istemci (. / CalculatorClient/bin/client.exe)  
  
        2.  Hesap Makinesi hizmetinin (. / CalculatorService/bin/service.exe)  
  
        3.  Yönlendirme Hizmeti (. / RoutingService/bin/RoutingService.exe)  
  
3.  Hesaplayıcı istemcisinde istemcisini başlatmak için ENTER tuşuna basın.  
  
     Şu çıktı görmeniz gerekir:  
  
    ```Output  
    Add(100,15.99) = 115.99  
    Subtract(145,76.54) = 68.46  
    Multiply(9,81.25) = 731.25  
    Divide(22,7) = 3.14285714285714  
    ```  
  
## <a name="configurable-via-code-or-appconfig"></a>Kod ya da App.config aracılığıyla yapılandırılabilir  
 Bir App.config dosyası yönlendiricinin davranışını tanımlamak için kullanmak üzere yapılandırılmış örnek verilir. Ayrıca tanınmıyor şekilde başka bir şey için App.config dosyasının adını değiştirin ve yöntem çağrısının açıklamasını kaldırın `ConfigureRouterViaCode()`. Her iki yöntem yönlendiriciden aynı davranışı sonuçlanır.  
  
### <a name="scenario"></a>Senaryo  
 Bu örnek bir protokol Köprüsü ve hata işleyici işlev gören hizmet yönlendirici gösterir. Bu senaryoda, hiçbir içerik tabanlı yönlendirme gerçekleştirilir; Yönlendirme hizmeti, iletileri doğrudan önceden yapılandırılmış bir hedef uç noktaları kümesine geçirmek için yapılandırılmış bir saydam proxy düğümü olarak görev yapar. Yönlendirme hizmeti de saydam onu çalıştığında, BT'nin Uç noktalara göndermek için ile iletişim kurmak için yapılandırılmış oluşan hataları işleme ek adımları gerçekleştirir. Yönlendirme hizmeti, Protokolü köprü olarak işlev gören dış iletişim için bir protokol ve iç iletişim için başka bir tanımlamak kullanıcı sağlar.  
  
### <a name="real-world-scenario"></a>Gerçek dünya senaryosu  
 Contoso bir birlikte çalışabilen Hizmeti uç noktası dünyaya performans dahili olarak en iyi duruma getirirken sağlamak istiyor. Bu nedenle hizmetlerinin dünyaya BasicHttpBinding dahili olarak yönlendirme hizmeti hizmetlerinin kullanmak NetTcpBinding kullanarak uç noktası bu bağlantısı birleştirmesi kullanırken bir uç nokta üzerinden kullanıma sunar. Ayrıca, kendi hizmet geçici kesinti kendi üretim herhangi birinde, dayanıklı olmasını teklifi Hizmetleri ve böylece Yönlendirici hizmetini kullanarak arkasında birden çok uç nokta sanallaştıran Contoso isteyen kullanıcının hata işleme otomatik olarak Yük Devretmesini özellikleri Yedekleme uç noktaları gerektiğinde.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric barındırma ve kalıcılığı örnekleri](http://go.microsoft.com/fwlink/?LinkId=193961)
