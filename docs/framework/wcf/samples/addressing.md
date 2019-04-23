---
title: Adres Ayarlama
ms.date: 03/30/2017
ms.assetid: d438e6f2-d0f3-43aa-b259-b51b5bda2e64
ms.openlocfilehash: a59c3b354404169c2baadd4ab8c2702728d9a891
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59767987"
---
# <a name="addressing"></a>Adres Ayarlama
Adresleme örnek çeşitli yönleri ve uç nokta adresleri özelliklerini gösterir. Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md). Bu örnekte hizmet kendiliğinden barındırılır. Hem hizmet hem de istemci konsol uygulamalardır. Hizmetin göreli ve mutlak uç nokta adresleri bir birleşimini kullanarak birden fazla uç nokta tanımlar.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Hizmet yapılandırma dosyasının temel adres ve dört uç noktanın belirtir. Temel adres, aşağıdaki örnek yapılandırmada gösterildiği gibi konak/service/baseAddresses altında Ekle öğesi kullanılarak belirtilir.  
  
```xml  
<service name="Microsoft.ServiceModel.Samples.CalculatorService"  
         behaviorConfiguration="CalculatorServiceBehavior">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />  
    </baseAddresses>  
  </host>  
</service>  
```  
  
 Aşağıdaki örnek yapılandırmada gösterilen ilk uç nokta tanımı taban adresini ve hizmetin göreli adresini URI oluşturma kuralları aşağıdaki uç nokta adresi olduğu anlamına gelir göreli bir adresi belirtir.  
  
```xml
<!-- Empty relative address specified:   
     use the base address provided by the host. -->  
<!-- The endpoint address is  
     http://localhost:8000/ServiceModelSamples/service. -->  
<endpoint address=""  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Bu durumda, göreli adresi boştur (""), uç nokta adresini temel adresi ile aynıdır. Gerçek bir uç nokta adresi `http://localhost:8000/servicemodelsamples/service`.
  
 İkinci uç nokta tanımı, ayrıca aşağıdaki örnek yapılandırmada gösterildiği gibi bir göreli adresini belirtir.  
  
```xml  
<!-- The relative address specified: use the base address -->  
<!-- provided by the host + path. The endpoint address is -->  
<!-- http://localhost:8000/servicemodelsamples/service/test. -->  
<endpoint address="/test"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Hizmetin göreli adresini "test" öğesine taban adresi olarak eklenir. Gerçek bir uç nokta adresi `http://localhost:8000/servicemodelsamples/service/test`.
  
 Aşağıdaki örnek yapılandırmada gösterildiği gibi üçüncü bir uç nokta tanımı mutlak bir adres belirtir.  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Temel adres, adres, hiçbir rol oynar. Gerçek bir uç nokta adresi `http://localhost:8001/hello/servicemodelsamples`.
  
 Mutlak bir adres ve farklı bir aktarım dördüncü uç nokta adresini belirtir; TCP. Temel adres, adres, hiçbir rol oynar. Gerçek bir uç nokta adresi `net.tcp://localhost:9000/servicemodelsamples/service`.
  
```xml  
<!-- The absolute address specified, different transport: -->  
<!-- use the specified address, and ignore the base address. -->  
<!-- The endpoint address is -->  
<!-- net.tcp://localhost:9000/servicemodelsamples/service. -->  
<endpoint address=  
          "net.tcp://localhost:9000/servicemodelsamples/service"  
          binding="netTcpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
</service>  
```  
  
 Dört hizmet uç noktaları yalnızca biri istemcisinin eriştiği, ancak tüm dört kendi yapılandırma dosyasında tanımlanır. Oluştururken istemci bir uç nokta seçer `CalculatorProxy` nesne. Yapılandırma adını değiştirerek `CalculatorEndpoint1` aracılığıyla `CalculatorEndpoint4`, her bir uç nokta alıştırma yapabilirsiniz.  
  
 Örneği çalıştırdığında, hizmet adı ve her biri kendi uç için sözleşme adı bağlama adresi numaralandırır. Meta veri değişimi (MEX) uç noktası başka bir uç nokta ServiceHost'ın açısından olduğundan listede görünür.  
  
```  
Service endpoints:  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service/test  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8001/hello/servicemodelsamples  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  net.tcp://localhost:9000/servicemodelsamples/service  
           binding:  NetTcpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service/mex  
           binding:  MetadataExchangeHttpBinding  
           contract: IMetadataExchange  
  
The service is ready.  
Press <ENTER> to terminate service.  
```  
  
 İstemci çalıştırdığınızda, işlem isteklerini ve yanıtlarını hem hizmet hem de istemci konsol pencerelerinde görüntülenir. Her konsol penceresi hizmet ve istemci kapatmak için ENTER tuşuna basın.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1. Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Bu örnek için yapılandırmayı yeniden üretmek için Svcutil.exe kullanma, istemci kodu eşleştirilecek istemci yapılandırmasında uç noktası adını değiştirmek emin olun.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Addressing`  
