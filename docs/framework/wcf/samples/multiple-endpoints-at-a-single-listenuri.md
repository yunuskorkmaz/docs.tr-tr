---
title: Bir ListenUri için Birden Fazla Belirteç
ms.date: 03/30/2017
ms.assetid: 911ffad4-4d47-4430-b7c2-79192ce6bcbd
ms.openlocfilehash: f3eb2036ffbb7c5e8cae77ebc1a86e07d31626c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="multiple-endpoints-at-a-single-listenuri"></a>Bir ListenUri için Birden Fazla Belirteç
Birden çok uç tek bir noktada barındıran bir hizmeti bu örnek gösteriyor `ListenUri`. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesap makinesi hizmetinin uygular.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Örnekte gösterildiği şekilde [birden çok uç nokta](../../../../docs/framework/wcf/samples/multiple-endpoints.md) örnek, bir hizmet birden çok uç nokta, her biri farklı adresleri ve büyük olasılıkla ayrıca farklı bağlamaları barındırabilir. Bu örnek aynı adresindeki birden fazla uç noktası ana bilgisayar mümkün olduğunu gösterir. Bu örnek ayrıca bir hizmet uç noktası olan adresleri iki tür arasındaki farklar gösterilmektedir: `EndpointAddress` ve `ListenUri`.  
  
 `EndpointAddress` Mantıksal bir hizmet adresidir. SOAP iletilerine ele alınan adresidir. `ListenUri` Fiziksel hizmet adresidir. Bağlantı noktası ve adres bilgilerini nerede hizmet uç noktası gerçekten iletileri geçerli makineye bekler sahiptir. Çoğu durumda, farklı bu adresler için gerek yoktur; zaman bir `ListenUri` açıkça belirtilmediği takdirde URI'si için varsayılan olarak `EndpointAddress` bitiş noktası. Bazı durumlarda, bunları ne zaman iletileri kabul edebilir bir yönlendirici yapılandırma farklı Hizmetleri sayıya ele gibi ayırt etmek kullanışlıdır.  
  
## <a name="service"></a>Hizmet  
 Bu örnek hizmetinde iki sözleşmeleri sahip `ICalculator` ve `IEcho`. Ek olarak her zamanki `IMetadataExchange` uç noktası, üç uygulama uç noktaları, aşağıdaki kodda gösterildiği gibi vardır.  
  
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
  
 Tüm üç bitiş noktaları aynı anda barındırılan `ListenUri` ve aynı `binding` -bitiş noktaları aynı `ListenUri` iletileri bu fiziksel adresindeki üzerinde dinleyen bir tek kanal yığını paylaşan olduğundan, aynı bağlama olması gerekir Makine. `address` Her uç noktasını URN; genellikle fiziksel konumlara adresleri temsil eden ancak adres eşleştirme ve bu örnekte gösterildiği gibi filtreleme amaçlı olarak kullanıldığından aslında adresi URI, her türlü olabilir.  
  
 Tüm üç bitiş noktaları aynı paylaştığından `ListenUri`, ileti geldiğinde Windows Communication Foundation (WCF) ileti hedefleyen için hangi uç noktaya, karar vermeniz gerekir. Her uç nokta iki bölümden oluşan bir ileti filtresi vardır: adresi filtresi ve sözleşme Filtresi. Adres filtre ile eşleşen `To` hizmet uç noktası adresine SOAP iletisi. Örneğin, yalnızca iletileri ele `To "Urn:OtherEcho"` bu hizmetin üçüncü uç noktası için bir aday değildir. Sözleşme filtresi belirli bir sözleşme işlemlerle ilişkili eylemler eşleşir. Örneğin, eylemiyle iletileri `IEcho`. `Echo` çünkü ikinci ve üçüncü uç noktalar için bu hizmetin sözleşme filtrelerle eşleşen Bu uç noktaları konak her ikisi de `IEcho` sözleşme.  
  
 Bu nedenle adresi filtresi ve sözleşme filtresi birleşimi, bu hizmetin ulaşan her ileti yolu mümkün kılar `ListenUri` doğru uç noktası. Diğer uç noktalarından farklı bir adresine gönderilen iletileri kabul ettiğinden üçüncü uç noktası diğer iki Ayrıştırılan. Birinci ve ikinci uç noktaları birbirinden sözleşmelerine (gelen ileti eylem) göre ayrılır.  
  
## <a name="client"></a>İstemci  
 Yalnızca iki farklı adresi uç sunucuda yüklü olduğu istemci uç noktalarını da iki adresine sahip. Hem sunucu hem de istemci mantıksal adresi adlı `EndpointAddress`. Ancak fiziksel adres adlı ancak `ListenUri` fiziksel adres sunucuda istemci adlı `Via`.  
  
 Sunucuda gibi varsayılan olarak, bu iki adres aynıdır. Belirtmek için bir `Via` uç noktanın adresinden farklı istemci üzerinde `ClientViaBehavior` kullanılır:  
  
```  
Uri via = new Uri("http://localhost/ServiceModelSamples/service.svc");  
CalculatorClient calcClient = new CalculatorClient();  
calcClient.ChannelFactory.Endpoint.Behaviors.Add(  
        new ClientViaBehavior(via));  
```  
  
 Her zamanki gibi adres Svcutil.exe tarafından oluşturulan istemci yapılandırma dosyasından birlikte gelir. `Via` (İçin karşılık geldiği `ListenUri` hizmetinin) hizmetin meta verilerde görünmez ve bu bilgileri istemci-bant (yalnızca gibi hizmetin meta veri adresi) için bildirilmesi gerekir.  
  
 Bu örnekte istemci iletileri gönderir her sunucunun üç uygulama uç noktaları için onun göstermek için ile iletişim kurabilmesini (ve ayırt) tüm üç uç noktaları, hepsi aynı olsa bile `Via`.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Çapraz-makine için Client.cs dosyasındaki localhost hizmeti makine adı ile değiştirmeniz gerekir.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpointsSingleUri`  
  
## <a name="see-also"></a>Ayrıca Bkz.
