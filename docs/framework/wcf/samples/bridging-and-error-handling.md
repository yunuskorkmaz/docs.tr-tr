---
title: Köprü Oluşturma ve Hata İşleme
ms.date: 03/30/2017
ms.assetid: 4ae87d1a-b615-4014-a494-a53f63ff0137
ms.openlocfilehash: 6afaddc75855b7e95ad708b2179cabb9aee35001
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43389074"
---
# <a name="bridging-and-error-handling"></a>Köprü Oluşturma ve Hata İşleme
Bu örnek, bir istemci farklı bağlamaları bir hizmeti arasındaki iletişimi köprüleme Windows Communication Foundation (WCF) yönlendirme hizmeti nasıl kullanıldığını gösterir. Bu örnek ayrıca yük devretme senaryosu için bir yedekleme hizmetin nasıl kullanılacağını gösterir. Yönlendirme hizmeti, içerik tabanlı bir yönlendirici uygulamanıza dahil etmek kolay bir WCF bileşenidir. Bu örnek, yönlendirme hizmeti kullanarak iletişim kurmak için standart WCF hesaplayıcı örnek uyum sağlar.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\ErrorHandlingAndBridging`  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Bu örnekte, hesaplayıcı istemci yönlendirici tarafından sunulan bir uç noktaya iletileri göndermek için yapılandırılır. Yönlendirme hizmeti, kendisine gönderilen tüm iletileri kabul etmesini ve hesaplayıcı hizmetine karşılık gelen bir uç nokta iletmek için yapılandırılır. Aşağıdaki noktaları birincil hesap makinesi hizmeti, yedekleme hesaplayıcı hizmet ve hesaplayıcı istemci ve hizmet ve istemci arasındaki iletişimin nasıl olacağını yapılandırmasını açıklamak yönlendirme hizmetini kullanarak:  
  
-   Hesaplayıcı istemci NetTcpBinding kullanılacak hesap makinesi hizmet yapılandırılırken BasicHttpBinding kullanmak için yapılandırılır. Otomatik olarak yönlendirme hizmeti hesaplayıcı hizmetine gönderilmeden önce ileti gerekli olarak dönüştürür ve hesaplayıcı istemci bunlara erişebilmesi için yanıtlar da dönüştürür.  
  
-   Yönlendirme hizmeti iki hesap makinesi hizmetleri hakkında bilir: birincil hesaplayıcı hizmeti ve yedekleme hesaplayıcı hizmeti. Yönlendirme hizmeti, ilk birincil hesaplayıcı hizmet uç noktası ile iletişime geçmeye çalışır. Basılı olan uç nokta nedeniyle bu girişim başarısız olursa, yönlendirme hizmeti, ardından yedekleme hesaplayıcı hizmet uç noktası ile iletişim kurmak çalışır.  
  
 Bu nedenle istemci tarafından gönderilen iletileri yönlendirici tarafından alınır ve gerçek hesaplayıcı hizmete yönlendirilir. Hesaplayıcı hizmet uç noktası kapalı ise, yönlendirme hizmeti iletiyi yedekleme hesaplayıcı hizmet uç noktasına yönlendirir. Yedekleme hesaplayıcı hizmetinden gelen iletileri geri sırayla bunları hesaplayıcı istemciye aktarır hizmet yönlendiriciye gönderilir.  
  
> [!NOTE]
>  Yedekleme listesini tanımlanmış birden fazla uç nokta olabilir. Bu durumda yedekleme Hizmeti uç noktası kapalı ise, yönlendirme hizmeti başarılı bir bağlantı gerçekleşene kadar listedeki sonraki yedekleme uç noktasına bağlanmak çalışır.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], RouterBridgingAndErrorHandling.sln açın.  
  
2.  Visual Studio'da F5'e ya da CTRL + SHIFT + B tuşuna basın  
  
    1.  Otomatik gerekli projeleri F5 tuşuna bastığınızda başlatma isterseniz, çözüme sağ tıklayın, **özellikleri**hem de **başlangıç projesi** düğümünde **OrtakÖzellikler**seçin **birden fazla başlangıç projesi**, tüm projeleri ayarlanmış ve **Başlat**.  
  
    2.  CTRL + SHIFT + B ile proje oluşturuyorsanız, aşağıdaki uygulamaları Başlat:  
  
        1.  Hesaplayıcı istemci (. / CalculatorClient/bin/client.exe)  
  
        2.  Hesaplayıcı hizmeti (. / CalculatorService/bin/service.exe)  
  
        3.  Yönlendirme Hizmeti (. / RoutingService/bin/RoutingService.exe)  
  
3.  Hesaplayıcı istemcisinde istemcisini başlatmak için ENTER tuşuna basın.  
  
     Aşağıdaki çıktıyı görmeniz gerekir:  
  
    ```Output  
    Add(100,15.99) = 115.99  
    Subtract(145,76.54) = 68.46  
    Multiply(9,81.25) = 731.25  
    Divide(22,7) = 3.14285714285714  
    ```  
  
## <a name="configurable-via-code-or-appconfig"></a>Kod veya App.config aracılığıyla yapılandırılabilir  
 Bir App.config dosyası yönlendiricinin davranışını tanımlamak için kullanmak üzere yapılandırılmış örnek verilir. Ayrıca App.config dosyasının adı bir şeye tanınmıyor şekilde değiştirin ve yöntem çağrısına açıklamasını kaldırın `ConfigureRouterViaCode()`. Her iki yöntem aynı davranışı yönlendiriciden sonuçlanır.  
  
### <a name="scenario"></a>Senaryo  
 Bu örnek, bir protokol Köprüsü ve hata işleyicisi davranan hizmet yönlendirici gösterir. Bu senaryoda hiçbir içerik tabanlı yönlendirme gerçekleşir; Yönlendirme hizmeti, iletileri doğrudan önceden yapılandırılmış bir hedef uç noktaları kümesine geçirmek için yapılandırılmış bir saydam proxy düğümü olarak görev yapar. Yönlendirme hizmeti de bunu çalıştığında uç noktalar için BT'nin göndermek için ile iletişim kurmak için yapılandırıldığı oluşan hataları şeffaf bir şekilde işleme ek adımları gerçekleştirir. Yönlendirme hizmeti Protokolü köprü olarak işlev gören dış iletişim için bir protokol, diğeri dahili iletişim için tanımlamak kullanıcı sağlar.  
  
### <a name="real-world-scenario"></a>Gerçek dünya senaryosu  
 Contoso, dahili olarak performansını iyileştirme sırasında bir birlikte hizmet uç noktası, dünya çapında sağlamak istiyor. Bu nedenle hizmetlerinin dünya çapında BasicHttpBinding dahili olarak yönlendirme hizmeti, bağlantı hizmetlerini kullanan NetTcpBinding kullanarak uç noktasına arasında köprü kuracak şekilde kullanırken bir uç nokta aracılığıyla kullanıma sunar. Ayrıca, Contoso geçici kesinti kendi üretim herhangi birinde, dayanıklı olacak şekilde, hizmet, hizmetleri ve bu nedenle kullanarak yönlendirici hizmeti arkasında birden fazla uç nokta sanallaştırır istediği kullanıcının hata işleme özelliklerini otomatik olarak yük devretme Yedekleme uç gerektiğinde.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric barındırma ve Kalıcılık örnekleri](https://go.microsoft.com/fwlink/?LinkId=193961)
