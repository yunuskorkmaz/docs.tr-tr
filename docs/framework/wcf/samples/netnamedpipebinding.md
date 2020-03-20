---
title: NetNamedPipeBinding
ms.date: 03/30/2017
helpviewer_keywords:
- Net Profile Named Pipe
ms.assetid: e78e845f-c325-46e2-927d-81616f97f7d5
ms.openlocfilehash: da54a835fd32efe4f53a80701465d2d7d8adba7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183471"
---
# <a name="netnamedpipebinding"></a>NetNamedPipeBinding
Bu örnek, `netNamedPipeBinding` aynı makinede çapraz proses iletişimi sağlayan bağlamayı gösterir. Adlandırılmış borular makineler arasında çalışmaz. Bu örnek, [Başlangıç](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesap makinesi hizmetine dayanmaktadır.  
  
 Bu örnekte, hizmet kendi kendine barındırılan. Hem istemci hem de hizmet konsol uygulamalarıdır.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Bağlama istemci ve hizmet için yapılandırma dosyalarında belirtilir. Bağlama türü, aşağıdaki `binding` örnek yapılandırmada gösterildiği gibi, [ \<istemci \<>öğesinin](../../configure-apps/file-schema/wcf/endpoint-of-client.md) [ \<bitiş noktası>](../../configure-apps/file-schema/wcf/endpoint-element.md) veya bitiş noktası> özniteliği içinde belirtilir:  
  
```xml  
<endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
          binding="netNamedPipeBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Önceki örnekte, varsayılan ayarlarla bağlamayı `netNamedPipeBinding` kullanmak için bir bitiş noktasının nasıl yapılandırılabildiğini gösterir. Bağlamayı `netNamedPipeBinding` yapılandırmak ve bazı ayarlarını değiştirmek istiyorsanız, bağlayıcı bir yapılandırma tanımlamanız gerekir. Bitiş noktası, öznitelik ile `bindingConfiguration` ada göre bağlama yapılandırmabaşvurugerekir.  
  
```xml  
<endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
          binding="netNamedPipeBinding"  
          bindingConfiguration="Binding1"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Bu örnekte, bağlama yapılandırması adlandırılır `Binding1` ve aşağıdaki tanımı vardır:  
  
```xml  
<bindings>  
  <!--   
        Following is the expanded configuration section for a NetNamedPipeBinding.  
        Each property is configured with the default value.  
     -->  
  <netNamedPipeBinding>  
    <binding name="Binding1"
             closeTimeout="00:01:00"  
             openTimeout="00:01:00"
             receiveTimeout="00:10:00"
             sendTimeout="00:01:00"  
             transactionFlow="false"
             transferMode="Buffered"
             transactionProtocol="OleTransactions"  
             hostNameComparisonMode="StrongWildcard"
             maxBufferPoolSize="524288"  
             maxBufferSize="65536"
             maxConnections="10"
             maxReceivedMessageSize="65536">  
      <security mode="Transport">  
        <transport protectionLevel="EncryptAndSign" />  
      </security>  
    </binding>  
  </netNamedPipeBinding>  
</bindings>  
```  
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
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
  
3. Örneği tek bir makine yapılandırmasında çalıştırmak [için, Windows Communication Foundation Samples'i çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\NamedPipe`  
