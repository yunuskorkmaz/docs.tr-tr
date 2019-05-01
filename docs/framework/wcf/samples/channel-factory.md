---
title: Kanal Fabrikası
ms.date: 03/30/2017
ms.assetid: 09b53aa1-b13c-476c-a461-e82fcacd2a8b
ms.openlocfilehash: 0bcaa739a51d168e18c809804b7da6948ab61e9d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62002423"
---
# <a name="channel-factory"></a>Kanal Fabrikası
Bu örnek, bir istemci uygulaması ile bir kanalı nasıl oluşturacağınızı gösterir. <xref:System.ServiceModel.ChannelFactory> yerine oluşturulmuş istemci sınıfı. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesaplayıcı hizmet uygulayan.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Bu örnekte <xref:System.ServiceModel.ChannelFactory%601> hizmet uç noktası için bir kanal oluşturmak için sınıf. Genellikle, bir hizmet uç noktası için bir kanal oluşturmak için bir istemci türü ile oluşturduğunuz [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ve oluşturulan türün bir örneğini oluşturun. Kullanarak bir kanalı oluşturabilirsiniz <xref:System.ServiceModel.ChannelFactory%601> , bu örnekte gösterildiği gibi sınıf. Aşağıdaki örnek kod tarafından oluşturulan hizmet hizmette aynı [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
```csharp  
EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
WSHttpBinding binding = new WSHttpBinding();  
ChannelFactory<ICalculator> factory = new   
                    ChannelFactory<ICalculator>(binding, address);  
ICalculator channel = factory.CreateChannel();  
```  
  
> [!IMPORTANT]
>  Bu örnek bir çapraz makine senaryosunda çalıştırıyorsanız, önceki kodda, "localhost" hizmetini çalıştıran makinenin tam adıyla değiştirmelisiniz. Bu örnek, bu kod yapılmalıdır için uç nokta adresi ayarlamak için yapılandırma kullanmaz.  
  
 Kanal oluşturulduktan sonra hizmet işlemleri ile oluşturulan bir istemci olarak çağrılabilir.  
  
```csharp  
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = channel.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```  
  
 Kanal kapatmak için önce için dönüştürülmelidir bir <xref:System.ServiceModel.IClientChannel> arabirimi. Oluşturulan kanal istemcisi kullanılarak uygulama bildirilmiş olmasıdır `ICalculator` yöntemleri olan arabirimi gibi `Add` ve `Subtract` ama `Close`. `Close` Yöntemi kaynaklanan üzerinde <xref:System.ServiceModel.ICommunicationObject> arabirimi.  
  
```csharp  
// Close the channel.  
 ((IClientChannel)client).Close();  
```  
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemci uygulamayı kapatın istemci penceresinde ENTER tuşuna basın.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1. Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md). Bu örnek meta veri yayımlama etkinleştirmez unutmayın. Meta veri yayımlama istemci türünü yeniden oluşturmak Bu örnek için önce etkinleştirmeniz gerekir.  
  
3. Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-cross-machine"></a>Örneği çalıştırmak için makine çapraz  
  
1. Aşağıdaki kodda "localhost" hizmetini çalıştıran makinenin tam adıyla değiştirin.  
  
    ```csharp  
    EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
    ```  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ChannelFactory`  
