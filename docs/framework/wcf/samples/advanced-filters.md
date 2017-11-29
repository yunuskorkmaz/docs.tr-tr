---
title: "Gelişmiş Filtreler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d81590f-e036-4f96-824a-4a187f462764
caps.latest.revision: "23"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0a9d7ce5029e0f5b95b98dd4f44e42f6c07bb8e1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="advanced-filters"></a>Gelişmiş Filtreler
Bu örnek gösteren bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] yönlendirme hizmeti. Yönlendirme hizmeti bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] içerik tabanlı yönlendirici uygulamanıza dahil kolaylaştırır bileşeni. Bu örnek standart uyum [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yönlendirme hizmeti kullanarak iletişim kurmak için hesap makinesi örnek. Bu örnek ileti filtreleri ve İleti Filtresi tabloları kullanılarak içerik tabanlı yönlendirme mantığını tanımlamak üzere nasıl gösterir.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedFilters`  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Aşağıdaki tabloda, yönlendirme hizmeti İleti Filtresi tabloya eklenen ileti filtreleri gösterir.  
  
|Filtrele|Kural|Öncelik|  
|------------|----------|--------------|  
|(Başlık varsa)|Yuvarlama|2|  
|Varsa (Ep2 üzerinde gösterilen)|Normal|1.|  
|Varsa (Adres2 ile gösterilmiştir)|Yuvarlama|1.|  
|Varsa (RoundRobin1)|Normal|0|  
|Varsa (RoundRobin2)|Yuvarlama|0|  
  
 İleti filtreleri ve İleti Filtresi tabloları oluşturulabilir ve kod aracılığıyla veya uygulama yapılandırma dosyasında yapılandırılmış. Bu örnek için ileti filtreleri ve kodlarda RoutingService\routing.cs dosyasında tanımlanan veya RoutingService\App.config dosya uygulama yapılandırma dosyasında tanımlanan İleti Filtresi tabloları bulabilirsiniz. Aşağıdaki paragraflara ileti filtreleri ve İleti Filtresi tabloları kod aracılığıyla bu örnek için nasıl oluşturulduğunu açıklar.  
  
 İlk olarak, bir <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> için özel üstbilgi arar. Unutmayın <xref:System.ServiceModel.WSHttpBinding> sonuçları SOAP 1.2 ad alanını kullanmak için tanımlanmış bir XPath ifadesi SOAP 1.2 kullanarak, Zarf sürümü. Varsayılan ad alanı yöneticisini <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>s zaten kullanılabilir /s12 SOAP 1.2 ad alanı için bir önek tanımlar. Ancak, varsayılan ad alanı yöneticisi bu önek tanımlanmalıdır böylece gerçek üstbilgi değerini tanımlamak için istemcinin kullandığı özel ad alanı yok. Bu başlığıyla görüntülenir herhangi bir iletisi bu filtre ile eşleşen.  
  
```  
XPathMessageContext namespaceManager = new XPathMessageContext();  
namespaceManager.AddNamespace("custom", "http://my.custom.namespace/");  
  
XPathMessageFilter xpathFilter = new XPathMessageFilter("/s12:Envelope/s12:Header/custom:RoundingCalculator = 1", namespaceManager);  
```  
  
 İkinci filtresi bir <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter>, alındı herhangi bir iletisi eşleşen `calculatorEndpoint`. Bir hizmet uç noktası nesnesi oluşturulduğunda, uç nokta adı tanımlanır.  
  
```  
EndpointNameMessageFilter endpointNameFilter = new EndpointNameMessageFilter("calculatorEndpoint");  
```  
  
 Üçüncü filtresi bir <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>. Bu uç noktada sağlanan adres ön eki (veya ön bölümü) eşleşen bir adres ile gösterilen herhangi bir iletisi eşleşir. Bu örnekte adres ön eki "http://localhost/routingservice/router/rounding/" tanımlanır. Başka bir deyişle, bu filtre tarafından gönderilen gelen iletiler için "http://localhost/routingservice/router/rounding/ *" eşleştirilir. Bu durumda, adresi "http://localhost/routingservice/router/rounding/calculator" olan yuvarlama hesaplayıcı noktadaki görünmesini iletileri olur.  
  
```  
PrefixEndpointAddressMessageFilter prefixAddressFilter = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://localhost/routingservice/router/rounding/"));  
```  
  
 Son iki ileti filtreleri özel <xref:System.ServiceModel.Dispatcher.MessageFilter>s. Bu örnekte, "RoundRobin" İleti Filtresi kullanılır. Bu ileti filtresi sağlanan RoutingService\RoundRobinMessageFilter.cs dosyasında oluşturulur. Aynı gruba ayarlandığında bu filtreler yalnızca bunlardan birinin yanıt şekilde ileti eşleşen ve bunlar yapmamanızı, raporlama arasında alternatif `true` birer birer.  
  
```  
RoundRobinMessageFilter roundRobinFilter1 = new RoundRobinMessageFilter("group1");  
  
RoundRobinMessageFilter roundRobinFilter2 = new RoundRobinMessageFilter("group1");  
```  
  
 Ardından, tüm bu iletilerin eklenen bir <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601>. Bunu yaparken öncelikleri İleti Filtresi tablosu filtreleri yürütür sırasını etkilemek için belirtilmiş. Filtre yürütülen öncelik o kadar yüksektir, çabuk; bir filtre yürütülen düşük önceliği, daha sonra. Bu nedenle öncelikle 2 bir filtre önce bir filtre 1 öncelikte çalışır. Belirtilmezse varsayılan öncelik düzeyi 0'dır. Bir ileti Filtresi tablosu verilen öncelik düzeyindeki tüm filtreleri sonraki en düşük öncelik düzeyi taşımadan önce yürütür. Bir eşleşme belirli bir öncelikte bulunursa, ardından İleti Filtresi tablosu eşleşmeleri sonraki daha düşük öncelikli olarak bulunmaya çalışılırken devam etmez.  
  
> [!NOTE]
>  Bu örnek İleti Filtresi öncelikleri kullanmayı gösterir, ancak genel olarak, daha fazla kullanıcı olduğunu ve tasarımı tasarım daha iyi ve düzgün çalışması için öncelik gerektirmeyen gibi filtrelerinizi yapılandırın.  
  
 Eklenecek ilk filtreyi XPath filtresi ve önceliği 2'ye ayarlanır. Yürütür ilk ileti filtresi budur. Ne diğer filtreler sonuçlarını olacağını, ne olursa olsun özel üstbilgi bulursa ileti yuvarlama hesaplayıcı uç noktasına yönlendirilir.  
  
 Öncelik 1 olduğunda, iki filtre eklenir. XPath filtresi öncelikli 2 ileti eşleşmiyorsa yeniden, bunlar yalnızca çalıştırın. Bu iki filtre gösterdi olduğunda ileti burada açıklanan belirlemek için iki farklı yolu gösterilmektedir. İki filtre etkili bir şekilde iletinin iki uç noktalardan biri ulaşmadığını denetleyin, bunların her ikisi de return çünkü bunlar aynı öncelik düzeyinde çalıştırılamıyor `true` aynı anda.  
  
 Son olarak, öncelikli RoundRobin çalıştırmak 0 (en düşük öncelik) filtreleri iletisi. Aynı ada sahip filtreler yapılandırıldığından, yalnızca bunlardan birinin aynı anda eşleşir. Özel Başlık sahip tüm iletiler yönlendirilir ve tüm bunları belirli sanallaştırılmış Uç noktalara ele RoundRobin ileti filtreler tarafından işlenen iletiler yalnızca varsayılan yönlendirici uç özel olmadan ele alınan iletileri olduklarından, Üstbilgi. Her çağrı için bir ileti üzerinde bu iletileri geçiş için işlemleri yarısı normal hesaplayıcı bitiş noktasına gidin ve diğer yarısı yuvarlama hesaplayıcı bitiş noktasına gidin.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], AdvancedFilters.sln açın.  
  
2.  Açmak için **Çözüm Gezgini**seçin **Çözüm Gezgini** gelen **Görünüm** menüsü.  
  
3.  F5 veya CTRL + SHIFT + B tuşuna basın [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].  
  
    1.  Otomatik gerekli projeleri F5 tuşuna bastığınızda başlatılan istediğiniz varsa, çözüme sağ tıklayın ve seçin **özellikleri**. Seçin **başlangıç projesi** düğümü altında **ortak özellikleri** sol bölmede. Seçin **birden fazla başlangıç projesi** radyo düğmesinin ve tüm projeleri için ayarlanmış **Başlat** eylem.  
  
    2.  CTRL + SHIFT + B projeyle oluşturuyorsanız, aşağıdaki uygulamalar başlatmanız gerekir:  
  
        1.  Hesaplayıcı istemci (. / CalculatorClient/bin/client.exe)  
  
        2.  Hesap Makinesi hizmetinin (. / CalculatorService/bin/service.exe)  
  
        3.  Yönlendirme hesap makinesi hizmetinin (. / RoundingCalcService/bin/service.exe)  
  
        4.  RoutingService (. / RoutingService/bin/RoutingService.exe)  
  
4.  Hesaplayıcı istemci konsol penceresinde istemcisini başlatmak için ENTER tuşuna basın. İstemci aralarından seçim yapabileceğiniz hedef uç noktaları listesini döndürür.  
  
5.  Karşılık gelen harfini yazarak bir hedef uç noktası seçin ve ENTER tuşuna basın.  
  
6.  Ardından, istemci bir özel üst bilgi eklemek isteyip istemediğinizi sorar. E'ye Evet veya Hayır, N ENTER tuşuna BASIN.  
  
7.  Yaptığınız seçimleri bağlı olarak, farklı bir çıktı görmeniz gerekir.  
  
    1.  Çıktı iletileri bir özel üst bilgi eklediyseniz döndürülen verilmiştir.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    2.  Özel üst bilgi içermeyen yuvarlama hesaplayıcı endpoint seçerseniz çıkış döndürülen verilmiştir.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    3.  Özel üstbilgi olmadan normal hesaplayıcı endpoint seçerseniz çıkış döndürülen verilmiştir.  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68. 46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
    4.  Özel üst bilgi içermeyen varsayılan yönlendirici endpoint seçerseniz çıkış döndürülen verilmiştir.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.14285714285714  
        ```  
  
8.  Hesaplayıcı hizmeti ve yuvarlama hesaplayıcı Hizmeti ayrıca yazdırır ilgili konsol pencerelerini çağrılan işlemlerinin bir günlük çıkışı.  
  
9. İstemci konsol penceresine `quit` ve çıkmak için ENTER tuşuna basın.  
  
10. Hizmetler konsolunda Windows Hizmetleri sonlandırmak için ENTER tuşuna basın.  
  
## <a name="configurable-via-code-or-appconfig"></a>Kod ya da App.config aracılığıyla yapılandırılabilir  
 Bir App.config dosyası yönlendiricinin davranışını tanımlamak için kullanmak üzere yapılandırılmış örnek verilir. Ayrıca RoutingService\App.config dosyasının adı başka bir şey için tanınmıyor şekilde değiştirin ve yöntem çağrısının açıklamasını kaldırın `ConfigureRouterViaCode()` RoutingService\routing.cs içinde. Her iki yöntem yönlendiriciden aynı davranışı sonuçlanır.  
  
### <a name="scenario"></a>Senaryo  
 Bu örnek, birden çok türleri veya hizmetleri uygulaması bir uç noktası aracılığıyla açığa çıkarılması izin vererek içerik tabanlı bir yönlendirici işlevi gören yönlendirici gösterir.  
  
### <a name="real-world-scenario"></a>Gerçek dünya senaryosu  
 Contoso tüm genel olarak, bunlar birden çok farklı türlerdeki Hizmetleri için erişim sunar tek bir uç nokta kullanıma sunmak için kendi Hizmetleri sanallaştırmayı istiyor. Bu durumda, gelen isteklerin gönderilmesi gerektiğini belirlemek için yönlendirme hizmetin içerik tabanlı Yönlendirme yetenekleri kullanın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric barındırma ve kalıcılığı örnekleri](http://go.microsoft.com/fwlink/?LinkId=193961)
