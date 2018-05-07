---
title: Gelişmiş Hata İşleme
ms.date: 03/30/2017
ms.assetid: ed54b687-78af-4eda-8507-9fd081bdea1a
ms.openlocfilehash: 035f15cb817e6a6a9ed54c56f4b848932a193ecf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="advanced-error-handling"></a>Gelişmiş Hata İşleme
Bu örnek Windows Communication Foundation (WCF) yönlendirme hizmeti gösteriyor. Yönlendirme hizmeti bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] içerik tabanlı yönlendirici uygulamanıza dahil kolaylaştırır bileşeni. Bu örnek nasıl yönlendirme hizmeti akıllıca hataları, işlemleri ve çok noktaya yayın gibi daha karmaşık diğer ileti kavramları kullanarak kurtarır gösterir.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedErrorHandling`  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Bu örnekte, yönlendirme hizmeti ileti bu iletiyi bir MSMQ sırası ve çok noktaya yayın için sıraların iki liste okumak için yapılandırılır. Bir liste için Hizmet Kuyrukları kullanılır ve başka bir günlük sıraları için kullanılır.  
  
 Varsayılan olarak, bağlaması MSMQ yönlendirme hizmeti için yapılandırılmış olduğundan, kullanım işlemleri kullanımını destekler, yönlendirme hizmeti ileti Gelen sırası (raporlamadan önce işlem ve her listedeki en az bir kuyruk tarafından alınan emin yapar `InQ`), iletiyi başarıyla yönlendirildi. Bu nedenle, her iki hizmet kuyrukları veya hem günlük sıra kullanılamaz olduğu durumda, ileti yönlendirilemeyen ve gelen sırası bazı işlemler yapması yönlendirme hizmeti raporlar. Bu eylem sistem sahipsiz sıraya ileti taşınırken oluşur.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  > [!IMPORTANT]
    >  Bu örneği çalıştırmadan önce MSMQ yükleyin. MSMQ yüklü değilse, bir özel durum iletisi örnek çalıştırırken döndürülür. MSMQ yüklemek için yönergeleri bulunabilir [yükleme Message Queuing (MSMQ)](http://go.microsoft.com/fwlink/?LinkId=166437).  
  
     Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], AdvancedErrorHandling.sln açın.  
  
2.  Tuşuna **F5** veya **CTRL + SHIFT + B** Visual Studio.  
  
    1.  CTRL + SHIFT + B uygulamasıyla yapılandırdıysanız, uygulamayı başlatmanız gerekir. / RoutingService/bin/debug/RoutingService.exe.  
  
3.  Konsol penceresinde istemcisini başlatmak için ENTER tuşuna basın.  
  
4.  İstemci, her örneği için kuyrukları farklı istatistikleri döndürür.  
  
    1.  Durum 1 (hata sayısı) için döndürülen çıktının verilmiştir.  
  
        ```Output  
        The inbound queue has 0 messages.  
        The primary service queue has 1 messages.   
        The backup service queue has 0 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <Enter> to continue  
        ```  
  
    2.  Durum 3 (birincil hizmet ve sıra hataları günlüğe kaydetme) için döndürülen çıktının verilmiştir.  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.   
        The backup service queue has 1 messages.   
        The primary logging queue does not exist.   
        The backup logging queue has 1 messages.   
        Press <ENTER> to continue.  
        ```  
  
    3.  Durum 4 (birincil hizmet sırası ve birincil ve yedek günlüğü sıra hatası) için döndürülen çıktının verilmiştir.  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 0 messages.   
        The primary logging queue does not exist.   
        The backup logging queue does not exist.   
        The System Dead Letter queue has 1 messages.   
        Press <ENTER> to Quit.  
        ```  
  
    4.  Durum 2 (birincil hizmet sırası arızası) için döndürülen çıktının verilmiştir.  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 1 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <ENTER> to continue.  
        ```  
  
## <a name="configurable-via-code-or-appconfig"></a>Kod ya da App.config aracılığıyla yapılandırılabilir  
 Bir App.config dosyası yönlendiricinin davranışını tanımlamak için kullanmak üzere yapılandırılmış örnek verilir. Ayrıca RoutingService\App.config dosyasının adı başka bir şey için tanınmıyor şekilde değiştirin ve değerini değiştirmek `configDriven` RoutingService\Program.cs için alanındaki `false` kod içinde tanımlanan yapılandırmasını kullanmak için. Her iki yöntem yönlendiriciden aynı davranışı sonuçlanır.  
  
### <a name="scenario"></a>Senaryo  
 Bu örnek, yönlendirme hizmeti işlemleri gibi gelişmiş Mesajlaşma işlevlerini işlemek ve içerik almak ve doğru hata senaryolarını işleme bir parçası olarak bu özellikleri kullanabilir gösterir.  
  
### <a name="real-world-scenario"></a>Gerçek dünya senaryosu  
 Gerekli tüm hizmetleri hata koşulları sırasında bile bilgi aldığından emin olmak üzere yönlendirme hizmeti aracılığıyla Contoso işlem kullanmak isterse alır. Ayrıca, bunların doğru ve otomatik olarak işlenecek hataları ve hata işleme mantığı bile ne zaman kullanıldığı bir ileti teslim edilemeyen durumda bildirilecek hataları ister. Bu amaçla belirli Uç noktalara beklendiği gibi devretmek için yönlendirme hizmeti yapılandırın ve yönlendirme hizmeti oluşturulması, tamamlama ve geri alma/durduruluyor işlemleri/alma bağlamlarının içeren hata durumları işleme gerekli.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric barındırma ve kalıcılığı örnekleri](http://go.microsoft.com/fwlink/?LinkId=193961)
