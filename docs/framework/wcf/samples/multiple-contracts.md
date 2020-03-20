---
title: Birden Fazla Sözleşme
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: ed59803b867dfe7994aceea010aa656c53927a0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144350"
---
# <a name="multiple-contracts"></a>Birden Fazla Sözleşme
Çoklu Sözleşmeler örneği, bir hizmette birden fazla sözleşmenin nasıl uygulanacağını ve uygulanan sözleşmelerin her biriyle iletişim kurmak için uç noktaların nasıl yapılandırılabildiğini gösterir. Bu örnek [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)dayanmaktadır. Hizmet, `ICalculator` sözleşme ve `ICalculatorSession` sözleşme olmak üzere iki sözleşmeyi tanımlamak üzere değiştirildi.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Hizmet sınıfı hem sözleşmeleri `ICalculator` `ICalculatorSession` hem de sözleşmeleri uygular. Sözleşmelerden biri oturum gerektirdiğinden, hizmet, <xref:System.ServiceModel.InstanceContextMode.PerSession> oturumun ömrü boyunca durumu korumak için örnek modunu kullanır.  
  
 Hizmet yapılandırması, her sözleşmeyi ortaya çıkarmak için iki uç nokta tanımlamak üzere değiştirildi. Bitiş `ICalculator` noktası, temel adreste bir `basicHttpBinding`. Bitiş `ICalculatorSession` noktası, aşağıdaki örnek yapılandırmada gösterildiği `wsHttpBinding` `bindingConfiguration` `BindingWithSession`gibi, öznitelik kümesine ayarlanmış bir öznitelik kullanılarak taban adreste/oturumda açığa gösterilir.  
  
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
  
 Oluşturulan istemci kodu artık hem özgün `ICalculator` sözleşme hem de `ICalculatorSession` yeni sözleşme için bir istemci sınıfı içerir. İstemci yapılandırması ve kodu, her sözleşmeyle uygun hizmet bitiş noktasında iletişim kurmak için değiştirildi.  
  
 İstemci bir konsol windows uygulamasıdır (.exe). Hizmet, Internet Information Services (IIS) tarafından barındırılır.  
  
 İstemci konsol penceresi, her uç noktaya gönderilen işlemleri, önce temel bitiş noktasını ve ardından güvenli bitiş noktasını görüntüler.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
