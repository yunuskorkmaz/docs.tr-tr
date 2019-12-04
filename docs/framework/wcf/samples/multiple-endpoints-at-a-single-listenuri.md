---
title: Bir ListenUri için Birden Fazla Belirteç
ms.date: 03/30/2017
ms.assetid: 911ffad4-4d47-4430-b7c2-79192ce6bcbd
ms.openlocfilehash: ef4212fa0989f80393f62119d9b2b6cda370ef94
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714728"
---
# <a name="multiple-endpoints-at-a-single-listenuri"></a>Bir ListenUri için Birden Fazla Belirteç
Bu örnek, tek bir `ListenUri`birden çok uç noktayı barındıran bir hizmeti gösterir. Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](../../../../docs/framework/wcf/samples/getting-started-sample.md) Başlarken hizmetini temel alır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 [Birden çok uç nokta](../../../../docs/framework/wcf/samples/multiple-endpoints.md) örneğinde gösterildiği gibi, bir hizmet, her biri farklı adreslere ve muhtemelen farklı bağlamalara sahip birden fazla uç nokta barındırabilir. Bu örnek, aynı adreste birden çok uç noktanın barındırmada mümkün olduğunu gösterir. Bu örnek ayrıca bir hizmet uç noktasının sahip olduğu iki tür adres arasındaki farklılıkları gösterir: `EndpointAddress` ve `ListenUri`.  
  
 `EndpointAddress`, bir hizmetin mantıksal adresidir. SOAP iletilerinin adreslendiği adrestir. `ListenUri`, hizmetin fiziksel adresidir. Hizmet uç noktasının geçerli makinedeki iletileri gerçekten dinlediği bağlantı noktası ve adres bilgileri bulunur. Çoğu durumda, bu adreslerin farklı olması gerekmez; `ListenUri` açıkça belirtilmediğinde, varsayılan olarak uç noktanın `EndpointAddress` URI 'sidir. Birkaç durumda, bir yönlendiriciyi yapılandırırken olduğu gibi farklı hizmetlere yönelik iletileri kabul edebilecek şekilde ayırt etmek yararlı olur.  
  
## <a name="service"></a>Hizmet  
 Bu örnekteki hizmette iki sözleşme, `ICalculator` ve `IEcho`vardır. Normal `IMetadataExchange` uç noktasına ek olarak, aşağıdaki kodda gösterildiği gibi üç uygulama uç noktası vardır.  
  
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
  
 Üç uç noktanın tümü aynı `ListenUri` barındırılır ve aynı `binding` uç noktaların aynı `ListenUri` aynı bağlama sahip olması gerekir, çünkü makinede o fiziksel adresteki iletileri dinleyen tek bir kanal yığınını paylaşıyor. Her uç noktanın `address` URN olur; genellikle adresler fiziksel konumları temsil ediyorsa, aslında adres, bu örnekte gösterildiği gibi eşleştirme ve filtreleme amaçları için kullanıldığından adres herhangi bir tür URI olabilir.  
  
 Üç uç noktanın tümü aynı `ListenUri`paylaştığından, bir ileti buraya ulaştığında, Windows Communication Foundation (WCF) iletinin hangi uç noktaya ait olduğunu karar vermelidir. Her uç noktanın iki bölümden oluşan bir ileti filtresi vardır: adres filtresi ve sözleşme filtresi. Adres filtresi, SOAP iletisinin `To` hizmet uç noktasının adresiyle eşleştirir. Örneğin, yalnızca `To "Urn:OtherEcho"` iletiler bu hizmetin üçüncü uç noktası için adaylardır. Sözleşme filtresi, belirli bir sözleşmenin işlemleriyle ilişkili eylemlerle eşleşir. Örneğin, `IEcho`eylemine sahip mesajlar. `Echo`, bu uç noktaların her ikisi de `IEcho` sözleşmesini barındırdığından bu hizmetin ikinci ve üçüncü bitiş noktalarının sözleşme filtreleriyle eşleşir.  
  
 Bu nedenle, adres filtresi ve sözleşme filtresi birleşimi, bu hizmetin `ListenUri` gelen her iletiyi doğru uç noktaya yönlendirmeye olanak tanır. Diğer uç noktalardan farklı bir adrese gönderilen iletileri kabul ettiğinden, üçüncü uç nokta diğer iki sunucudan farklılaştırılabilir. Birinci ve ikinci uç noktalar, sözleşmeleri (gelen ileti eylemi) temel alınarak birbirinden farklılaştırılır.  
  
## <a name="client"></a>İstemci  
 Sunucudaki uç noktaların iki farklı adresi olduğu gibi, istemci uç noktalarında da iki adres vardır. Hem sunucu hem de istemcide, mantıksal adrese `EndpointAddress`denir. Ancak fiziksel adrese sunucuda `ListenUri` çağrıldığında, istemcide fiziksel adrese `Via`adı verilir.  
  
 Sunucuda olduğu gibi, varsayılan olarak bu iki adres aynıdır. İstemcide bitiş noktasının adresinden farklı bir `Via` belirtmek için, `ClientViaBehavior` kullanılır:  
  
```csharp  
Uri via = new Uri("http://localhost/ServiceModelSamples/service.svc");  
CalculatorClient calcClient = new CalculatorClient();  
calcClient.ChannelFactory.Endpoint.Behaviors.Add(  
        new ClientViaBehavior(via));  
```  
  
 Her zamanki gibi, adres, Svcutil. exe tarafından oluşturulan istemci yapılandırma dosyasından gelir. `Via` (hizmetin `ListenUri` karşılık gelen), hizmetin meta verilerinde görünmez ve bu nedenle bu bilgilerin istemciye bant dışı (hizmetin meta veri adresi gibi) bildirilmesi gerekir.  
  
 Bu örnekteki istemci, her bir sunucunun üç uygulama uç noktasına ileti gönderir ve bunların hepsi aynı `Via`sahip olsa da üç uç nokta ile iletişim kurabildiğini gösterir.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
    > [!NOTE]
    > Çapraz makine için, Client.cs dosyasındaki localhost 'u hizmet makinesinin adıyla değiştirmelisiniz.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpointsSingleUri`  
