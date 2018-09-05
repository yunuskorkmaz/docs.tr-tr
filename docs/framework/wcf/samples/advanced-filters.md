---
title: Gelişmiş Filtreler
ms.date: 03/30/2017
ms.assetid: 8d81590f-e036-4f96-824a-4a187f462764
ms.openlocfilehash: 7022384e8abe93f4276eec48785b3243ed926438
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43564206"
---
# <a name="advanced-filters"></a>Gelişmiş Filtreler
Bu örnek, bir Windows Communication Foundation (WCF) yönlendirme hizmeti gösterir. Yönlendirme hizmeti, içerik tabanlı bir yönlendirici uygulamanıza dahil etmek kolay bir WCF bileşenidir. Bu örnek, yönlendirme hizmeti kullanarak iletişim kurmak için standart WCF hesaplayıcı örnek uyum sağlar. Bu örnek, içerik tabanlı yönlendirme mantığı kullanarak ileti filtreleri ve İleti Filtresi tabloları tanımlama gösterir.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedFilters`  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Aşağıdaki tablo, yönlendirme hizmeti İleti Filtresi tabloya eklenen ileti filtreleri gösterir.  
  
|Filtrele|Kural|Öncelik|  
|------------|----------|--------------|  
|(Üst bilgi varsa)|Yuvarlama|2|  
|Varsa (Ep2 üzerinde gösterilen)|Normal|1.|  
|Varsa (Adres2 ile gösterilmiştir)|Yuvarlama|1.|  
|Varsa (RoundRobin1)|Normal|0|  
|Varsa (RoundRobin2)|Yuvarlama|0|  
  
 İleti filtreleri ve İleti Filtresi tabloları oluşturulur ve kod aracılığıyla ya da uygulama yapılandırma dosyasında yapılandırılmış. Bu örnek için kodu RoutingService\routing.cs dosyasında aracılığıyla tanımlanan veya RoutingService\App.config dosyasında uygulama yapılandırma dosyasında tanımlanan İleti Filtresi tablo ve ileti filtreleri bulabilirsiniz. Aşağıdaki paragraflara İleti Filtresi tablo ve ileti filtreleri için bu örnek kod aracılığıyla nasıl oluşturulduğunu açıklar.  
  
 İlk olarak, bir <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> için özel üstbilgi görünür. Unutmayın <xref:System.ServiceModel.WSHttpBinding> sonuçları SOAP 1.2, SOAP 1.2 ad alanını kullanacak şekilde tanımlanan bir XPath ifadesi kullanarak, Zarf sürümü. Varsayılan ad alanı yöneticisini <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>s zaten kullanılabilen /s12 SOAP 1.2 ad alanı için bir önek tanımlar. Ancak, varsayılan ad alanı yöneticisi, bu ön eki tanımlanmalıdır bu nedenle, gerçek üstbilgi değerinin tanımlamak için istemcinin kullandığı özel ad alanı yok. Bu filtre ile bu üstbilgi görünür herhangi bir ileti eşleşir.  
  
```  
XPathMessageContext namespaceManager = new XPathMessageContext();  
namespaceManager.AddNamespace("custom", "http://my.custom.namespace/");  
  
XPathMessageFilter xpathFilter = new XPathMessageFilter("/s12:Envelope/s12:Header/custom:RoundingCalculator = 1", namespaceManager);  
```  
  
 İkinci filtre bir <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter>, herhangi bir ileti alındı eşleşen `calculatorEndpoint`. Uç nokta adı, bir hizmet uç noktası nesnesi oluşturulurken tanımlanır.  
  
```  
EndpointNameMessageFilter endpointNameFilter = new EndpointNameMessageFilter("calculatorEndpoint");  
```  
  
 Üçüncü filtre bir <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>. Bu, bir uç noktada adres ön eki (veya ön bölümü) koşuluyla eşleşen bir adres ile hatırlarsınız herhangi bir ileti ile eşleşir. Bu örnekte, adres ön eki olarak tanımlanan "http://localhost/routingservice/router/rounding/". İçin gönderilen tüm gelen iletileri buna "http://localhost/routingservice/router/rounding/*" Bu filtreden eşleştirilir. Bu durumda, yuvarlama hesaplayıcı noktadaki görünmesini iletileri olduğu adresi olan "http://localhost/routingservice/router/rounding/calculator".  
  
```  
PrefixEndpointAddressMessageFilter prefixAddressFilter = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://localhost/routingservice/router/rounding/"));  
```  
  
 Son iki ileti filtreleri özel <xref:System.ServiceModel.Dispatcher.MessageFilter>s. Bu örnekte, "RoundRobin" İleti Filtresi kullanılır. Bu ileti filtresi sağlanan RoutingService\RoundRobinMessageFilter.cs dosyasında oluşturulur. Aynı gruba ayarlandığında, bu filtreler yalnızca bunlardan birinin yanıt verdiği, ileti eşleştiğinden ve bunlar yapmamanızı, raporlama arasında alternatif `true` birer güncelleştirir.  
  
```  
RoundRobinMessageFilter roundRobinFilter1 = new RoundRobinMessageFilter("group1");  
  
RoundRobinMessageFilter roundRobinFilter2 = new RoundRobinMessageFilter("group1");  
```  
  
 Ardından, tüm iletiler için eklenen bir <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601>. Bunun yapılması, İleti Filtresi tablosu filtreleri yürütür sırasını etkilemek için öncelikleri belirtilir. Filtre yürütülür öncelik o kadar yüksektir, çabuk; bir filtre yürütülür düşük önceliği, daha sonra. Böylece öncelik 2 sırasında bir filtre önce bir filtre 1 öncelikli olarak çalışır. Belirtilmemişse varsayılan öncelik düzeyi 0'dır. İleti filtreleme tablosu tüm filtreleri verilen öncelik düzeyinde sonraki en düşük öncelik düzeyi taşımadan önce yürütür. Belirli bir öncelik bir eşleşme bulunursa, ardından İleti Filtresi tablosu sonraki daha düşük öncelikli olarak bulmaya çalışırken devam etmez.  
  
> [!NOTE]
>  Bu örnek İleti Filtresi öncelikleri kullanma işlemini gösterir, ancak genel olarak, daha yüksek performanslı ve daha iyi bir tasarım tasarım ve sağlayacak şekilde düzgün çalışması için öncelik gerektirmez, filtreleri yapılandırma.  
  
 Eklenecek ilk filtre XPath filtresi ve önceliği 2'ye ayarlanıyor. Yürütülen ilk ileti filtresi budur. Ne diğer filtrelerle sonuçlarını olacağını, ne olursa olsun üst bulursa ileti yuvarlama hesaplayıcı uç noktaya yönlendirilir.  
  
 Öncelik 1, iki filtre eklenir. İleti önceliği 2 sırasında XPath filtresi ile eşleşmiyorsa yeniden, bu yalnızca çalıştırın. Bu iki filtre, açılırken ileti burada açıklanan belirlemek için iki farklı yollar gösterilmiştir. İletinin iki uç noktalardan biri ulaşmadığını görmek için iki filtre etkili bir şekilde kontrol edin çünkü ikisi birden değil dönüş çünkü bunlar aynı öncelik düzeyinde çalıştırılabilir `true` aynı anda.  
  
 Son olarak, öncelik 0 (en düşük önceliğe) RoundRobin çalıştırmak için filtreler ileti. Aynı ada sahip filtreler yapılandırıldığından, bunlardan yalnızca biri aynı anda eşleşir. Özel üst bilgi sahip tüm iletiler yönlendirilir ve tüm bunları belirli sanallaştırılmış Uç noktalara yönelik RoundRobin ileti filtreler tarafından işlenen iletilerin yalnızca varsayılan yönlendirici uç noktasına özel olmadan ele alınan iletileri olduklarından, üst bilgisi. Bu iletiler bir iletinin her çağrı için geçiş işlemleri yarısını normal hesaplayıcı bitiş noktasına gidin ve diğer yarısı yuvarlama hesaplayıcı bitiş noktasına gidin.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], AdvancedFilters.sln açın.  
  
2.  Açmak için **Çözüm Gezgini**seçin **Çözüm Gezgini** gelen **görünümü** menüsü.  
  
3.  Visual Studio'da F5'e ya da CTRL + SHIFT + B tuşlarına basın.  
  
    1.  Otomatik gerekli projeleri F5 tuşuna bastığınızda başlatma isterseniz, çözüme sağ tıklayıp seçin **özellikleri**. Seçin **başlangıç projesi** düğümünde **ortak özellikler** sol bölmesinde. Seçin **birden fazla başlangıç projesi** radyo düğmesini ve tüm projeler için **Başlat** eylem.  
  
    2.  CTRL + SHIFT + B ile proje oluşturuyorsanız, aşağıdaki uygulamalar başlatmanız gerekir:  
  
        1.  Hesaplayıcı istemci (. / CalculatorClient/bin/client.exe)  
  
        2.  Hesaplayıcı hizmeti (. / CalculatorService/bin/service.exe)  
  
        3.  Yönlendirme hesaplayıcı hizmeti (. / RoundingCalcService/bin/service.exe)  
  
        4.  RoutingService (. / RoutingService/bin/RoutingService.exe)  
  
4.  Hesaplayıcı istemci konsol penceresinde istemcisini başlatmak için ENTER tuşuna basın. İstemci, aralarından seçim yapabileceğiniz hedef uç noktaları listesi döndürür.  
  
5.  Bir hedef uç noktası, karşılık gelen bir harf yazarak seçin ve ENTER tuşuna basın.  
  
6.  Ardından, istemci özel bir başlık eklemek isteyip istemediğimi sorar. Tuşuna Evet veya Hayır, N ENTER tuşuna BASIN.  
  
7.  Yaptığınız seçimlere bağlı olarak, farklı bir çıktı görmeniz gerekir.  
  
    1.  Çıkış iletileri için özel bir başlık eklediyseniz döndürülen verilmiştir.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    2.  Özel üst bilgi içermeyen yuvarlama hesaplayıcı uç nokta seçerseniz çıkış döndürülen verilmiştir.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    3.  Özel üst bilgi içermeyen normal hesaplayıcı uç nokta seçerseniz çıkış döndürülen verilmiştir.  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68. 46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
    4.  Özel üst bilgi içermeyen yönlendirici varsayılan uç nokta seçerseniz çıkış döndürülen verilmiştir.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.14285714285714  
        ```  
  
8.  Hesaplayıcı hizmetini ve yuvarlama hesaplayıcı hizmetini de yazdırır ilgili konsol pencerelerini çağrılan işlem günlüğünü dışarı.  
  
9. İstemci konsol penceresine `quit` çıkmak için ENTER tuşuna basın.  
  
10. Hizmetleri sonlandırmak için hizmetler Konsolu pencerelerinde ENTER tuşuna basın.  
  
## <a name="configurable-via-code-or-appconfig"></a>Kod veya App.config aracılığıyla yapılandırılabilir  
 Bir App.config dosyası yönlendiricinin davranışını tanımlamak için kullanmak üzere yapılandırılmış örnek verilir. Ayrıca RoutingService\App.config dosya adını bir şeye tanınmıyor şekilde değiştirin ve yöntem çağrısına açıklamasını kaldırın `ConfigureRouterViaCode()` RoutingService\routing.cs içinde. Her iki yöntem aynı davranışı yönlendiriciden sonuçlanır.  
  
### <a name="scenario"></a>Senaryo  
 Bu örnek, birden çok türleri veya uygulama hizmetleri bir uç nokta sağlamak ve içerik tabanlı bir yönlendirici görevi gören yönlendirici gösterir.  
  
### <a name="real-world-scenario"></a>Gerçek dünya senaryosu  
 Contoso tüm genel olarak, birden çok farklı türlerdeki Hizmetleri erişim sundukları tek bir uç nokta kullanıma sunmak için kendi hizmetlerini sanallaştırılması istemektedir. Bu durumda, gelen istekleri nereye gönderileceğini belirlemek için yönlendirme hizmetin içerik tabanlı yönlendirme becerilerinden.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric barındırma ve Kalıcılık örnekleri](https://go.microsoft.com/fwlink/?LinkId=193961)
