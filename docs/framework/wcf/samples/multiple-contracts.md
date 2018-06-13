---
title: Birden Fazla Sözleşme
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: 8e96d1ac27eb69d8e7e4da76aa8679aa35bf8ad4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33501743"
---
# <a name="multiple-contracts"></a>Birden Fazla Sözleşme
Birden fazla sözleşme örnek bir hizmette birden fazla sözleşme gerçekleştirme ve her uygulanan sözleşmeleri ile iletişim kurmak için bitiş noktalarını yapılandırmak nasıl gösterilir. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md). İki sözleşmelerini tanımlamak için hizmet değiştirilmiş `ICalculator` sözleşme ve `ICalculatorSession` sözleşme.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Hizmet sınıfı hem uygulayan `ICalculator` ve `ICalculatorSession` sözleşmeleri. Hizmet sözleşmeleri birini oturumu gerektirdiğinden, kullanır <xref:System.ServiceModel.InstanceContextMode.PerSession> oturum ömrü boyunca durumunu korumak üzere örnek modu.  
  
 Hizmet yapılandırması, her sözleşme kullanıma sunmak için iki uç noktalarını tanımlamak için değiştirildi. `ICalculator` Endpoint gösterilir taban adresi kullanarak bir `basicHttpBinding`. `ICalculatorSession` Endpoint gösterilir baseaddress/oturum kullanarak bir `wsHttpBinding` ile `bindingConfiguration` özniteliğini `BindingWithSession`, aşağıdaki örnek yapılandırmada gösterildiği gibi.  
  
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
  
 Oluşturulan istemci kodu artık hem özgün için bir istemci sınıfı içerir `ICalculator` sözleşme ve yeni `ICalculatorSession` sözleşme. İstemci yapılandırma ve kodun uygun hizmet uç noktada her sözleşme ile iletişim kurmak için değiştirilmiş.  
  
 İstemci bir konsol windows (.exe) uygulamasıdır. Hizmet, Internet Information Services (IIS) tarafından barındırılır.  
  
 İstemci konsol penceresi, her uç noktaları için önce güvenli bitiş noktası tarafından izlenen temel uç nokta gönderilen işlemleri görüntüler.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
  
## <a name="see-also"></a>Ayrıca Bkz.
