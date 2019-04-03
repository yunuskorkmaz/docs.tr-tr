---
title: Birden Fazla Sözleşme
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: 5e52c83d69c15ca5c407240a8971248205fef832
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818347"
---
# <a name="multiple-contracts"></a>Birden Fazla Sözleşme
Birden çok sözleşme örnek nasıl bir hizmet birden fazla sözleşmesini uygulama ve uç noktaları her uygulanan sözleşmelerin ile iletişim kurmak için yapılandırma gösterir. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md). Hizmet, iki sözleşmelerini tanımlamak için değiştirilmiş `ICalculator` sözleşme ve `ICalculatorSession` sözleşme.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Hizmet sınıfı her ikisini birden uygular `ICalculator` ve `ICalculatorSession` sözleşmeler. Sözleşmeler birini oturum gerektirdiğinden, hizmetin kullandığı <xref:System.ServiceModel.InstanceContextMode.PerSession> oturumunun ömrü boyunca durumunu korumak üzere örnek modu.  
  
 Her sözleşme kullanıma sunmak için iki uç nokta tanımlamak için hizmet yapılandırması değiştirildi. `ICalculator` Uç nokta Internet'e açık taban adresi kullanarak bir `basicHttpBinding`. `ICalculatorSession` Uç nokta kullanarak baseaddress/oturum sırasında sunulan bir `wsHttpBinding` ile `bindingConfiguration` özniteliğini `BindingWithSession`aşağıdaki örnek yapılandırmada gösterildiği gibi.  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <!-- ICalculator endpoint is exposed using BasicBinding at the base  
       address provided by host:   
       http://localhost/servicemodelsamples/service.svc  -->  
  <endpoint address=""  
            binding="basicHttpBinding"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  <!-- ICalculatorSession endpoint is exposed using BindingWithSession  
       at {baseaddress}/session:  
       http://localhost/servicemodelsamples/service.svc/session -->  
  <endpoint address="session"  
            binding="wsHttpBinding"  
            bindingConfiguration="BindingWithSession"   
           contract="Microsoft.ServiceModel.Samples.ICalculatorSession" />  
  ...  
</service>  
```  
  
 Oluşturulan istemci kodu artık istemci sınıfı hem özgün içerir `ICalculator` sözleşme ve yeni `ICalculatorSession` sözleşme. İstemci Yapılandırması ve kodu uygun hizmet uç noktasında her sözleşme ile iletişim kurmak için değiştirildi.  
  
 Bir konsol windows uygulaması (.exe) istemcisidir. Hizmet, Internet Information Services (IIS) tarafından barındırılır.  
  
 İlk gönderilen her uç nokta güvenli bir uç noktası tarafından izlenen temel uç nokta işlemleri istemci konsol penceresinde görüntüler.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
  
