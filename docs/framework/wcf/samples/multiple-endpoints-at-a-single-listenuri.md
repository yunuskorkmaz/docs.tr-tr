---
title: Bir ListenUri için Birden Fazla Belirteç
ms.date: 03/30/2017
ms.assetid: 911ffad4-4d47-4430-b7c2-79192ce6bcbd
ms.openlocfilehash: 8e26cc18ed35c446dda120c678dd7e879c756c0f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183480"
---
# <a name="multiple-endpoints-at-a-single-listenuri"></a>Bir ListenUri için Birden Fazla Belirteç
Bu örnek, tek `ListenUri`bir noktada birden çok uç noktayı barındıran bir hizmeti gösterir. Bu örnek, bir hesap makinesi hizmeti uygulayan [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md) dayanır.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 [Birden çok Uç Nokta](../../../../docs/framework/wcf/samples/multiple-endpoints.md) örneğinde gösterildiği gibi, bir hizmet her biri farklı adreslere ve büyük olasılıkla farklı bağlamalara sahip birden çok uç nokta barındırabilir. Bu örnek, aynı adreste birden çok uç nokta barındırmanın mümkün olduğunu gösterir. Bu örnek, bir hizmet bitiş noktasının sahip olduğu iki tür `EndpointAddress` adres `ListenUri`arasındaki farkları da gösterir: ve .  
  
 Bir `EndpointAddress` hizmetin mantıksal adresidir. SOAP mesajlarının adresolduğu adrestir. Hizmetin `ListenUri` fiziksel adresidir. Hizmet bitiş noktasının geçerli makinedeki iletileri gerçekten dinlediği bağlantı noktası ve adres bilgilerine sahiptir. Çoğu durumda, bu adreslerin farklı olmasına gerek yoktur; a `ListenUri` açıkça belirtilmemişse, bitiş noktasının `EndpointAddress` URI'sine varsayılan olarak Birkaç durumda, bir yönlendirici, farklı hizmetler bir dizi adresli iletileri kabul edebilir yapılandırma gibi bunları ayırt etmek yararlıdır.  
  
## <a name="service"></a>Hizmet  
 Bu örnekteki hizmetin iki `ICalculator` `IEcho`sözleşmesi vardır ve . Alışılmış `IMetadataExchange` bitiş noktasına ek olarak, aşağıdaki kodda gösterildiği gibi üç uygulama bitiş noktası vardır.  
  
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
  
 Her üç uç nokta da `ListenUri` aynı şekilde `binding` barındırılır ve `ListenUri` aynı uç noktaları kullanır - aynı uç noktalar aynı bağlamaya sahip olmalıdır, çünkü makinedeki fiziksel adresteki iletileri dinleyen tek bir kanal yığınını paylaşıyorlar. Her `address` bitiş noktasının bir URN'si; genellikle adresler fiziksel konumları temsil etse de, adres bu örnekte gösterildiği gibi eşleştirme ve filtreleme amacıyla kullanıldığından, adres her türlü URI olabilir.  
  
 Üç uç nokta da `ListenUri`aynı olduğundan , bir ileti geldiğinde, Windows Communication Foundation (WCF) iletinin kaderinde olan bitiş noktasına karar vermelidir. Her uç noktanın iki bölümden oluşan bir ileti filtresi vardır: adres filtresi ve sözleşme filtresi. Adres filtresi, `To` SOAP iletisinin hizmet bitiş noktasının adresiyle eşleşir. Örneğin, yalnızca bu hizmetin üçüncü bitiş noktası için adaylar yalnızca adreslenir. `To "Urn:OtherEcho"` Sözleşme filtresi, belirli bir sözleşmenin işlemleriyle ilişkili Eylemlerle eşleşir. Örneğin, eylemi ile iletileri `IEcho`. `Echo`bu uç noktaların her ikisi de sözleşmeyi barındırdığından, bu hizmetin `IEcho` hem ikinci hem de üçüncü uç noktalarının sözleşme filtrelerini eşleşir.  
  
 Böylece adres filtresi ve sözleşme filtresi nin birleşimi, bu hizmete `ListenUri` gelen her iletiyi doğru bitiş noktasına yönlendirmeyi mümkün kılar. Üçüncü uç nokta, diğer uç noktalardan farklı bir adrese gönderilen iletileri kabul ettiği için diğer ikisinden ayrılır. Birinci ve ikinci uç noktalar, sözleşmelerine (gelen iletinin Eylemi) göre birbirinden ayrılır.  
  
## <a name="client"></a>İstemci  
 Sunucudaki uç noktaların iki farklı adresi olduğu gibi, istemci uç noktalarının da iki adresi vardır. Hem sunucuda hem de istemcide, `EndpointAddress`mantıksal adres . Ancak fiziksel adres `ListenUri` sunucuda, istemcide ise fiziksel adrese . `Via`  
  
 Sunucuda olduğu gibi, varsayılan olarak, bu iki adres aynıdır. Uç noktanın adresinden `Via` `ClientViaBehavior` farklı bir istemci üzerinde bir belirtmek için kullanılır:  
  
```csharp  
Uri via = new Uri("http://localhost/ServiceModelSamples/service.svc");  
CalculatorClient calcClient = new CalculatorClient();  
calcClient.ChannelFactory.Endpoint.Behaviors.Add(  
        new ClientViaBehavior(via));  
```  
  
 Her zamanki gibi, adres Svcutil.exe tarafından oluşturulan istemci yapılandırma dosyasından gelir. `Via` (Hizmetin `ListenUri` karşısına karşılık gelen) hizmetin meta verilerinde görünmez ve bu nedenle bu bilgilerin bant dışı istemciye iletilmesi gerekir (hizmetin meta veri adresi gibi).  
  
 Bu örnekteki istemci, sunucunun üç uygulama uç noktasının her birine, hepsi aynı `Via`olmasına rağmen üç uç noktayla da iletişim kurabileceğini (ve ayırt edebildiği) iletiler gönderir.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
    > [!NOTE]
    > Çapraz makine için, Client.cs dosyasındaki localhost'u servis makinesinin adı ile değiştirmeniz gerekir.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpointsSingleUri`  
