---
title: Adres Ayarlama
ms.date: 03/30/2017
ms.assetid: d438e6f2-d0f3-43aa-b259-b51b5bda2e64
ms.openlocfilehash: 55bb30ba3df80e41986b1337f8732dd8ad3231ff
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463763"
---
# <a name="addressing"></a>Adres Ayarlama
Adresleme örneği, uç nokta adreslerinin çeşitli yönlerini ve özelliklerini gösterir. Örnek [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)dayanmaktadır. Bu örnekte hizmet kendi kendine barındırılır. Hem hizmet hem de istemci konsol uygulamalarıdır. Hizmet, göreli ve mutlak uç nokta adreslerinin bir birleşimini kullanarak birden çok uç nokta tanımlar.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Hizmet yapılandırma dosyası nda bir temel adres ve dört uç nokta belirtilir. Temel adres, aşağıdaki örnek yapılandırmada gösterildiği gibi hizmet/ana bilgisayar/baseAddresss altında ekle öğesi kullanılarak belirtilir.  
  
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
  
 Aşağıdaki örnek yapılandırmada gösterilen ilk uç nokta tanımı göreceli bir adres belirtir, bu da bitiş noktası adresinin temel adres ile URI kompozisyonunun kurallarını izleyen göreli adresin birleşimi olduğu anlamına gelir.  
  
```xml
<!-- Empty relative address specified:   
     use the base address provided by the host. -->  
<!-- The endpoint address is  
     http://localhost:8000/ServiceModelSamples/service. -->  
<endpoint address=""  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Bu durumda, göreli adres boş (""), bu nedenle bitiş noktası adresi temel adresle aynıdır. Gerçek bitiş noktası `http://localhost:8000/servicemodelsamples/service`adresi .
  
 İkinci uç nokta tanımı, aşağıdaki örnek yapılandırmada gösterildiği gibi göreli bir adres de belirtir.  
  
```xml  
<!-- The relative address specified: use the base address -->  
<!-- provided by the host + path. The endpoint address is -->  
<!-- http://localhost:8000/servicemodelsamples/service/test. -->  
<endpoint address="/test"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Göreli adres, "test", temel adrese eklenir. Gerçek bitiş noktası `http://localhost:8000/servicemodelsamples/service/test`adresi .
  
 Üçüncü uç nokta tanımı, aşağıdaki örnek yapılandırmada gösterildiği gibi mutlak bir adres belirtir.  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Temel adres adreste hiçbir rol oynamaz. Gerçek bitiş noktası `http://localhost:8001/hello/servicemodelsamples`adresi .
  
 Dördüncü uç nokta adresi mutlak bir adres ve farklı bir aktarım belirtir—TCP. Temel adres adreste hiçbir rol oynamaz. Gerçek bitiş noktası `net.tcp://localhost:9000/servicemodelsamples/service`adresi .
  
```xml  
<!-- The absolute address specified, different transport: -->  
<!-- use the specified address, and ignore the base address. -->  
<!-- The endpoint address is -->  
<!-- net.tcp://localhost:9000/servicemodelsamples/service. -->  
<endpoint address=  
          "net.tcp://localhost:9000/servicemodelsamples/service"  
          binding="netTcpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 İstemci dört hizmet uç noktasından yalnızca birine erişir, ancak dördü de yapılandırma dosyasında tanımlanır. İstemci `CalculatorProxy` nesneyi oluştururken bir bitiş noktası seçer. Yapılandırma adını `CalculatorEndpoint1` buradan `CalculatorEndpoint4`değiştirerek, uç noktaların her birini egzersiz yapabilirsiniz.  
  
 Örneği çalıştırdığınızda, hizmet, bitiş noktalarının her biri için adresi, bağlama adını ve sözleşme adını diziler. Meta veri değişimi (MEX) bitiş noktası, ServiceHost'un bakış açısından yalnızca başka bir bitiş noktasıdır, bu nedenle listede gösterir.  
  
```console  
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
  
 İstemciyi çalıştırdığınızda, işlem istekleri ve yanıtları hem hizmet hem de istemci konsolu pencerelerinde görüntülenir. Hizmeti ve istemciyi kapatmak için her konsol penceresinde ENTER tuşuna basın.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
    > [!NOTE]
    > Bu örnek için yapılandırmayı yeniden oluşturmak için Svcutil.exe kullanıyorsanız, istemci yapılandırmasındaki uç nokta adını istemci koduyla eşleşecek şekilde değiştirdiğinden emin olun.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Addressing`  
