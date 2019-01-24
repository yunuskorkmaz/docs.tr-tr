---
title: Bir ListenUri için Birden Fazla Belirteç
ms.date: 03/30/2017
ms.assetid: 911ffad4-4d47-4430-b7c2-79192ce6bcbd
ms.openlocfilehash: fbf636acf5e2cf4ef0f417b6b50a93d3e25c3ea6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643474"
---
# <a name="multiple-endpoints-at-a-single-listenuri"></a>Bir ListenUri için Birden Fazla Belirteç
Bu örnek, birden çok uç tek bir noktada barındıran bir hizmeti gösterir `ListenUri`. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesaplayıcı hizmet uygulayan.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Örnekte gösterildiği şekilde [birden fazla uç nokta](../../../../docs/framework/wcf/samples/multiple-endpoints.md) örnek, birden fazla uç noktası, her farklı adresleri ve belki de farklı bağlamaları ile bir hizmeti barındırabilir. Bu örnek, birden fazla uç nokta aynı adresten barındırmak mümkün olduğunu gösterir. Bu örnek ayrıca iki tür hizmet uç noktası olan adresler arasındaki farklar gösterir: `EndpointAddress` ve `ListenUri`.  
  
 `EndpointAddress` Hizmet mantıksal adresidir. SOAP iletilerini ele alınır adresidir. `ListenUri` Hizmet fiziksel adresidir. Bağlantı noktası ve adres bilgilerini, burada hizmet uç noktası gerçekten geçerli makine iletileri dinler sahiptir. Çoğu durumda, farklı bu adresler için gerek yoktur; olduğunda bir `ListenUri` açıkça belirtilmezse, URI değerini varsayılan olarak `EndpointAddress` uç nokta. Bazı durumlarda, iletileri kabul edebilirsiniz bir yönlendirici yapılandırma birtakım farklı hizmetler ele gibi bunları ayırt etmek kullanışlıdır.  
  
## <a name="service"></a>Hizmet  
 Bu hizmette iki sözleşmeleri olduğunu `ICalculator` ve `IEcho`. Ek olarak her zamanki `IMetadataExchange` uç noktası, aşağıdaki kodda gösterildiği gibi üç uygulama uç noktaları olan.  
  
```xml  
<endpoint address="urn:Stuff"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.ICalculator"   
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
<endpoint address="urn:Stuff"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IEcho"   
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
<endpoint address="urn:OtherEcho"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IEcho"   
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
```  
  
 Üç tüm uç noktalar aynı anda barındırılan `ListenUri` ve aynı `binding` -bitiş noktaları aynı `ListenUri` fiziksel Bu adresteki iletileri için dinlediği bir tek kanal yığını paylaşan çünkü aynı bağlama sahip olmalıdır Makine. `address` Her uç noktasını bir URN; genellikle fiziksel konumlara adresleri temsil eder, ancak eşleştirme ve bu örnekte gösterildiği gibi filtreleme amaçlı adresi kullanıldığından aslında adresi URI, herhangi bir türden olabilir.  
  
 Üç tüm uç noktalar aynı paylaştığından `ListenUri`, ileti geldiğinde Windows Communication Foundation (WCF) ileti için atanmış hangi uç noktaya, karar vermeniz gerekir. İki bölümden oluşan bir ileti filtresi her uç nokta vardır: adres filtresi ve sözleşme Filtresi. Eşleşen adresi filtre `To` hizmet uç noktası adresine SOAP iletisi. Örneğin, yalnızca iletileri ele `To "Urn:OtherEcho"` bu hizmetin üçüncü uç noktası için adaylardır. Sözleşme filtre, belirli bir sözleşme işlemleriyle ilişkili eylemler eşleşir. Örneğin, eylemi ile iletileri `IEcho`. `Echo` çünkü bu hizmet uç noktaları ikinci ve üçüncü sözleşme filtrelerle eşleşen her ikisi de bu uç noktaları konak `IEcho` sözleşme.  
  
 Bu nedenle adresi filtresi ve sözleşme filtresi birleşimi, bu hizmetin ulaşan her ileti yolu mümkün kılar `ListenUri` doğru uç noktaya. Diğer uç noktalardan gelen farklı bir adrese gönderilen iletileri kabul ettiğinden üçüncü uç noktası diğer iki Ayrıştırılan. Birinci ve ikinci uç noktalarını birbirinden sözleşmelerine (gelen ileti eylem) göre ayrılır.  
  
## <a name="client"></a>İstemci  
 Yalnızca sunucu uç noktalarda iki farklı adres olduğuna göre istemci uç noktalarını da iki adreslerine sahiptir. Hem sunucu hem de istemci mantıksal adresi çağrılır `EndpointAddress`. Ancak fiziksel adresiyle çağrılır ancak `ListenUri` fiziksel adresiyle sunucuda, istemcide çağrılır `Via`.  
  
 Sunucuda gibi varsayılan olarak, bu iki adres aynıdır. Belirtmek için bir `Via` uç noktanın adresinden farklı istemcide `ClientViaBehavior` kullanılır:  
  
```csharp  
Uri via = new Uri("http://localhost/ServiceModelSamples/service.svc");  
CalculatorClient calcClient = new CalculatorClient();  
calcClient.ChannelFactory.Endpoint.Behaviors.Add(  
        new ClientViaBehavior(via));  
```  
  
 Her zamanki şekilde svcutil.exe'yi oluşturulan istemci yapılandırma dosyasından adresi gelir. `Via` (Karşılık gelen `ListenUri` hizmetinin) hizmetin meta verilerinde görünmez ve bu bilgileri istemci-bant (olduğu gibi hizmetin meta veri adresi) bildirilmesi gerekir.  
  
 Bu örnekte istemci iletiler gönderen her sunucunun üç uygulama uç noktaları için BT'nin göstermek için kullanabilirsiniz ile iletişim (ve birbirinden) üç tüm uç noktalar, bunların tümü aynı olmasına rağmen `Via`.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Çapraz makine için Client.cs dosyasındaki localhost hizmeti makine adını değiştirmeniz gerekir.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpointsSingleUri`  
  
## <a name="see-also"></a>Ayrıca bkz.
