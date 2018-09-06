---
title: Gelişmiş Hata İşleme
ms.date: 03/30/2017
ms.assetid: ed54b687-78af-4eda-8507-9fd081bdea1a
ms.openlocfilehash: 72fb9885408759f5781501b548f81625d258d13c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43745264"
---
# <a name="advanced-error-handling"></a>Gelişmiş Hata İşleme
Bu örnek, Windows Communication Foundation (WCF) yönlendirme hizmeti gösterir. Yönlendirme hizmeti, içerik tabanlı bir yönlendirici uygulamanıza dahil etmek kolay bir WCF bileşenidir. Bu örnek nasıl yönlendirme hizmeti akıllı bir şekilde işlemleri ve çok noktaya yayın gibi daha karmaşık diğer ileti kavramları kullanarak hataları, kurtarır gösterir.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedErrorHandling`  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Bu örnekte, yönlendirme hizmeti, bir ileti bir MSMQ sırası ve çok noktaya yayın bu ileti kuyrukları iki listelerine okumak için yapılandırılır. Hizmet kuyruklar için kullanılan bir listesi ve başka bir günlük kuyruklar için kullanılır.  
  
 Varsayılan olarak, bağlama MSMQ yönlendirme hizmeti için yapılandırılmış olduğundan, işlem kullanımını destekler, yönlendirme hizmeti ileti raporlama için gelen kuyruğu (önce işlem ve her bir listedeki en az bir kuyruk tarafından alınan olmasını sağlar `InQ`), iletiyi başarıyla yönlendirildi. Bu nedenle, günlük kuyruklar hem de Hizmet Kuyrukları veya kullanılamaz olduğu durumlarda, yönlendirme hizmeti, ileti yönlendirilemeyen ve gelen sıra bazı işlemler yapması bildirir. Bu eylem, ileti sistemi edilemeyen iletiler sırasına taşıyarak oluşur.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  > [!IMPORTANT]
    >  Bu örneği çalıştırmadan önce MSMQ yükleyin. MSMQ yüklü değilse, örnek çalıştırılırken bir özel durum iletisi döndürülür. MSMQ yüklemek için yönergeler bulunabilir [yükleme Message Queuing (MSMQ)](https://go.microsoft.com/fwlink/?LinkId=166437).  
  
     Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], AdvancedErrorHandling.sln açın.  
  
2.  Tuşuna **F5** veya **CTRL + SHIFT + B** Visual Studio'da.  
  
    1.  CTRL + SHIFT + B ile bir uygulama oluşturuyorsanız, uygulamayı başlamalıdır. / RoutingService/bin/debug/RoutingService.exe.  
  
3.  Konsol penceresinde istemcisini başlatmak için ENTER tuşuna basın.  
  
4.  İstemci her çalışması için kuyruklar farklı İstatistikler döndürür.  
  
    1.  1 (hata sayısı) çalışması için döndürülen çıkış verilmiştir.  
  
        ```Output  
        The inbound queue has 0 messages.  
        The primary service queue has 1 messages.   
        The backup service queue has 0 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <Enter> to continue  
        ```  
  
    2.  3 (birincil hizmeti ve kuyruk hataları günlüğe kaydetme) çalışması için döndürülen çıkış verilmiştir.  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.   
        The backup service queue has 1 messages.   
        The primary logging queue does not exist.   
        The backup logging queue has 1 messages.   
        Press <ENTER> to continue.  
        ```  
  
    3.  4 (birincil hizmet kuyruğu ve birincil ve yedek günlük sıra hataları) çalışması için döndürülen çıkış verilmiştir.  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 0 messages.   
        The primary logging queue does not exist.   
        The backup logging queue does not exist.   
        The System Dead Letter queue has 1 messages.   
        Press <ENTER> to Quit.  
        ```  
  
    4.  2 (birincil hizmet sırası hatası) çalışması için döndürülen çıkış verilmiştir.  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 1 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <ENTER> to continue.  
        ```  
  
## <a name="configurable-via-code-or-appconfig"></a>Kod veya App.config aracılığıyla yapılandırılabilir  
 Bir App.config dosyası yönlendiricinin davranışını tanımlamak için kullanmak üzere yapılandırılmış örnek verilir. Ayrıca RoutingService\App.config dosya adını bir şeye tanınmıyor şekilde değiştirin ve değerini değiştirme `configDriven` için RoutingService\Program.cs alanındaki `false` kod içinde tanımlanan yapılandırmasını kullanmak için. Her iki yöntem aynı davranışı yönlendiriciden sonuçlanır.  
  
### <a name="scenario"></a>Senaryo  
 Yönlendirme hizmeti işlemleri gibi gelişmiş Mesajlaşma işlevlerini işlemek ve bağlamını alır ve bu özelliklerin doğru hata senaryolarını işleme işleminin bir parçası olarak kullanabilir, bu örnek gösterir.  
  
### <a name="real-world-scenario"></a>Gerçek dünya senaryosu  
 Contoso işlem kullanmak isterse, gerekli tüm hizmetleri bile sırasında hata koşulları bilgilerini almasını sağlamak için yönlendirme hizmeti aracılığıyla alır. Ayrıca, bunların doğru ve otomatik olarak işlenecek hataları ve hata durumunda bile hata işleme mantığı ne zaman kullanılır, bir iletinin teslim edilemeyen olduğunu bildirilmesini ister. Bu amaç için bunlar belirli Uç noktalara beklendiği gibi yük devretmek için yönlendirme hizmeti yapılandırın ve yönlendirme hizmeti oluşturma, tamamlama ve geri alma/iptal etme işlemleri ve alma bağlamları içeren hata durumları işler. gerekli.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric barındırma ve Kalıcılık örnekleri](https://go.microsoft.com/fwlink/?LinkId=193961)
