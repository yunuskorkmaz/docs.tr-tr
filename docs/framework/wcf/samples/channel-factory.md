---
title: "Kanal Fabrikası"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09b53aa1-b13c-476c-a461-e82fcacd2a8b
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7f5fb22c329bf7b27c32f05a2d8e41734723f53b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="channel-factory"></a>Kanal Fabrikası
Bu örnek bir istemci uygulaması bir kanal ile nasıl oluşturabileceğinizi gösterir <xref:System.ServiceModel.ChannelFactory> oluşturulan bir istemci yerine sınıfı. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesap makinesi hizmetinin uygular.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Bu örnekte <xref:System.ServiceModel.ChannelFactory%601> hizmet uç noktası için bir kanal oluşturmak için sınıfı. Genellikle, bir hizmet uç noktası için bir kanal oluşturmak için bir istemci türü ile oluşturduğunuz [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ve oluşturulan türünün bir örneği oluşturun. Kullanarak bir kanal oluşturabilirsiniz <xref:System.ServiceModel.ChannelFactory%601> Bu örnekte gösterildiği gibi sınıfı. Aşağıdaki örnek kod tarafından oluşturulan hizmet ile hizmeti aynı [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
```  
EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
WSHttpBinding binding = new WSHttpBinding();  
ChannelFactory<ICalculator> factory = new   
                    ChannelFactory<ICalculator>(binding, address);  
ICalculator channel = factory.CreateChannel();  
```  
  
> [!IMPORTANT]
>  Bu örnek bir makineler arası senaryosunda çalıştırıyorsanız, önceki kod "localhost" hizmetini çalıştıran bilgisayarın tam adı ile değiştirmeniz gerekir. Bu örnek, bu kodda yapılmalıdır için uç nokta adresi ayarlamak için yapılandırma kullanmaz.  
  
 Kanalı oluşturduktan sonra hizmet işlemleri yalnızca olarak oluşturulan bir istemci ile çağrılabilir.  
  
```  
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = channel.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```  
  
 Kanal kapatmak için öncelikle için dönüştürülmelidir bir <xref:System.ServiceModel.IClientChannel> arabirimi. Oluşturulan kanalı kullanılarak istemci uygulama bildirildiğinden budur `ICalculator` yöntemlerine sahiptir arabirimi gibi `Add` ve `Subtract` ama `Close`. `Close` Yöntemi kaynaklandığı <xref:System.ServiceModel.ICommunicationObject> arabirimi.  
  
```  
// Close the channel.  
 ((IClientChannel)client).Close();  
```  
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemci uygulamayı kapatın İstemcisi penceresinde ENTER tuşuna basın.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md). Bu örnek meta veri yayımlama etkinleştirmez unutmayın. Meta veri yayımlama istemci türü yeniden oluşturmak için bu örnek için önce etkinleştirmeniz gerekir.  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-cross-machine"></a>Örneği çalıştırmak için makine arası  
  
1.  Aşağıdaki kodda "localhost" hizmetini çalıştıran bilgisayarın tam adı ile değiştirin.  
  
    ```  
    EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
    ```  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ChannelFactory`  
  
## <a name="see-also"></a>Ayrıca Bkz.
