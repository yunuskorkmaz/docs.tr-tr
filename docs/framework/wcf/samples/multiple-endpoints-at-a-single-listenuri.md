---
title: Bir ListenUri için Birden Fazla Belirteç
ms.date: 03/30/2017
ms.assetid: 911ffad4-4d47-4430-b7c2-79192ce6bcbd
ms.openlocfilehash: 91220c6631db2f283b6571fbc32af2211feeaa35
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602498"
---
# <a name="multiple-endpoints-at-a-single-listenuri"></a>Bir ListenUri için Birden Fazla Belirteç
Bu örnek tek seferde birden çok uç noktayı barındıran bir hizmeti gösterir `ListenUri` . Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](getting-started-sample.md) Başlarken hizmetini temel alır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 [Birden çok uç nokta](multiple-endpoints.md) örneğinde gösterildiği gibi, bir hizmet, her biri farklı adreslere ve muhtemelen farklı bağlamalara sahip birden fazla uç nokta barındırabilir. Bu örnek, aynı adreste birden çok uç noktanın barındırmada mümkün olduğunu gösterir. Bu örnek ayrıca, bir hizmet uç noktasının sahip olduğu iki tür adres arasındaki farklılıkları gösterir: `EndpointAddress` ve `ListenUri` .  
  
 , `EndpointAddress` Bir hizmetin mantıksal adresidir. SOAP iletilerinin adreslendiği adrestir. `ListenUri`Hizmetin fiziksel adresidir. Hizmet uç noktasının geçerli makinedeki iletileri gerçekten dinlediği bağlantı noktası ve adres bilgileri bulunur. Çoğu durumda, bu adreslerin farklı olması gerekmez; açık bir `ListenUri` şekilde belirtilmediğinde, varsayılan olarak `EndpointAddress` uç noktanın URI 'sidir. Birkaç durumda, bir yönlendiriciyi yapılandırırken olduğu gibi farklı hizmetlere yönelik iletileri kabul edebilecek şekilde ayırt etmek yararlı olur.  
  
## <a name="service"></a>Hizmet  
 Bu örnekteki hizmette iki sözleşme vardır `ICalculator` ve `IEcho` . Normal uç noktasına ek olarak, `IMetadataExchange` aşağıdaki kodda gösterildiği gibi üç uygulama uç noktası vardır.  
  
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
  
 Üç uç noktanın hepsi aynı anda barındırılır `ListenUri` ve aynı `binding` bağlantı noktalarından aynı `ListenUri` olmalıdır, çünkü makinede o fiziksel adresteki iletileri dinleyen tek bir kanal yığınını paylaşıyor. `address`Her uç noktanın BIR urn olması gerekir; ancak genellikle adresler fiziksel konumları temsil ediyorsa, aslında bu örnekte gösterildiği gibi eşleştirme ve filtreleme amaçları için kullanıldığından adres herhangi bir tür URI olabilir.  
  
 Üç uç noktanın hepsi aynı şekilde paylaştığı için, `ListenUri` bir ileti buraya ulaştığında Windows Communication Foundation (WCF) iletinin hangi uç noktaya ait olduğunu karar vermelidir. Her uç noktanın iki bölümden oluşan bir ileti filtresi vardır: adres filtresi ve sözleşme filtresi. Adres filtresi, `To` SOAP iletisi ile hizmet uç noktasının adresiyle eşleşir. Örneğin, yalnızca belirtilen mesajlar `To "Urn:OtherEcho"` Bu hizmetin üçüncü uç noktası için adaylardır. Sözleşme filtresi, belirli bir sözleşmenin işlemleriyle ilişkili eylemlerle eşleşir. Örneğin, eylemine sahip mesajlar `IEcho` . `Echo`Bu uç noktaların her ikisi de sözleşmeyi barındırdığından, bu hizmetin ikinci ve üçüncü uç noktalarının sözleşme filtreleriyle eşleşir `IEcho` .  
  
 Bu nedenle, adres filtresi ve sözleşme filtresi birleşimi, bu hizmete ulaşan her iletiyi `ListenUri` doğru uç noktaya yönlendirmeye olanak tanır. Diğer uç noktalardan farklı bir adrese gönderilen iletileri kabul ettiğinden, üçüncü uç nokta diğer iki sunucudan farklılaştırılabilir. Birinci ve ikinci uç noktalar, sözleşmeleri (gelen ileti eylemi) temel alınarak birbirinden farklılaştırılır.  
  
## <a name="client"></a>İstemci  
 Sunucudaki uç noktaların iki farklı adresi olduğu gibi, istemci uç noktalarında da iki adres vardır. Hem sunucu hem de istemcide, mantıksal adres olarak adlandırılır `EndpointAddress` . Ancak fiziksel adres `ListenUri` sunucuda, istemci üzerinde, fiziksel adrese olarak adlandırılır `Via` .  
  
 Sunucuda olduğu gibi, varsayılan olarak bu iki adres aynıdır. `Via`Uç noktanın adresinden farklı bir istemcide belirtmek için `ClientViaBehavior` kullanılır:  
  
```csharp  
Uri via = new Uri("http://localhost/ServiceModelSamples/service.svc");  
CalculatorClient calcClient = new CalculatorClient();  
calcClient.ChannelFactory.Endpoint.Behaviors.Add(  
        new ClientViaBehavior(via));  
```  
  
 Her zamanki gibi, adres, Svcutil. exe tarafından oluşturulan istemci yapılandırma dosyasından gelir. `Via`(Hizmetin bu öğesine karşılık gelen `ListenUri` ), hizmetin meta verilerinde görünmez ve bu nedenle bu bilgilerin istemciye bant dışı iletilmesi gerekir (tıpkı hizmetin meta veri adresine benzer).  
  
 Bu örnekteki istemci her bir sunucunun üç uygulama uç noktasına ileti gönderir ve bunların hepsi aynı olsa da üç uç noktanın tümünü ayırt edebildiğini gösterir `Via` .  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
    > [!NOTE]
    > Çapraz makine için, Client.cs dosyasındaki localhost 'u hizmet makinesinin adıyla değiştirmelisiniz.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpointsSingleUri`  
