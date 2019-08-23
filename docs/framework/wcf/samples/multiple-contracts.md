---
title: Birden Fazla Sözleşme
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: 39970f9f0aefa46c3d064b39c9b35d195ef22843
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930357"
---
# <a name="multiple-contracts"></a>Birden Fazla Sözleşme
Birden çok sözleşme örneği, bir hizmette birden fazla sözleşmenin nasıl uygulanacağını ve uygulanan sözleşmelerin her biriyle iletişim kurmak için uç noktaların nasıl yapılandırılacağını gösterir. Bu örnek, [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)' i temel alır. Hizmet iki sözleşme, `ICalculator` sözleşme `ICalculatorSession` ve sözleşme tanımlamak üzere değiştirilmiştir.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Hizmet sınıfı hem hem de `ICalculator` `ICalculatorSession` sözleşmelerini uygular. Sözleşmelerden biri bir oturum gerektirdiğinden hizmet, oturumun kullanım ömrü boyunca durumu <xref:System.ServiceModel.InstanceContextMode.PerSession> korumak için örnek modunu kullanır.  
  
 Hizmet yapılandırması, her sözleşmeyi göstermek için iki uç nokta tanımlamak üzere değiştirilmiştir. Uç nokta, `basicHttpBinding`kullanarak temel adreste gösterilir. `ICalculator` Uç nokta, aşağıdaki örnek yapılandırmada gösterildiği gibi `bindingConfiguration` , özniteliği olarak `wsHttpBinding` `BindingWithSession`ayarlanmış bir ile kullanılarak BaseAddress/Session üzerinde gösterilir. `ICalculatorSession`  
  
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
  
 Oluşturulan istemci kodu artık özgün `ICalculator` sözleşme ve yeni `ICalculatorSession` sözleşme için bir istemci sınıfı içerir. İstemci yapılandırması ve kodu, uygun hizmet uç noktasındaki her bir sözleşmeyle iletişim kuracak şekilde değiştirilmiştir.  
  
 İstemci bir konsol Windows uygulaması (. exe). Hizmet, Internet Information Services (IIS) tarafından barındırılır.  
  
 İstemci konsolu penceresinde, ilk uç nokta, ardından güvenli uç nokta gelen uç noktalara gönderilen işlemler görüntülenir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
>  Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
