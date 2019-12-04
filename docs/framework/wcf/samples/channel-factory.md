---
title: Kanal Fabrikası
ms.date: 03/30/2017
ms.assetid: 09b53aa1-b13c-476c-a461-e82fcacd2a8b
ms.openlocfilehash: eac315cf88b2ecc7471f194ef6c3be902b3ccbaa
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716040"
---
# <a name="channel-factory"></a>Kanal Fabrikası

Bu örnek, bir istemci uygulamanın oluşturulan istemci yerine <xref:System.ServiceModel.ChannelFactory> sınıfıyla bir kanal nasıl oluşturacağınızı gösterir. Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](../../../../docs/framework/wcf/samples/getting-started-sample.md) Başlarken hizmetini temel alır.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

Bu örnek, bir hizmet uç noktasına kanal oluşturmak için <xref:System.ServiceModel.ChannelFactory%601> sınıfını kullanır. Genellikle, bir hizmet uç noktasına kanal oluşturmak için, [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ile bir istemci türü oluşturun ve oluşturulan türün bir örneğini oluşturun. Ayrıca, bu örnekte gösterildiği gibi <xref:System.ServiceModel.ChannelFactory%601> sınıfını kullanarak bir kanal oluşturabilirsiniz. Aşağıdaki örnek kod tarafından oluşturulan hizmet, [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)hizmeti ile aynıdır.

```csharp
EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");
WSHttpBinding binding = new WSHttpBinding();
ChannelFactory<ICalculator> factory = new
                    ChannelFactory<ICalculator>(binding, address);
ICalculator channel = factory.CreateChannel();
```

> [!IMPORTANT]
> Bu örneği bir çapraz makine senaryosunda çalıştırıyorsanız, yukarıdaki koddaki "localhost" hizmetini hizmeti çalıştıran makinenin tam adı ile değiştirmelisiniz. Bu örnek, uç nokta adresini ayarlamak için yapılandırma kullanmaz, bu nedenle bu işlem kodda yapılmalıdır.

Kanal oluşturulduktan sonra, hizmet işlemleri, oluşturulan bir istemcide olduğu gibi çağrılabilir.

```csharp
// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = channel.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
```

Kanalı kapatmak için öncelikle bir <xref:System.ServiceModel.IClientChannel> arabirimine atamalısınız. Bunun nedeni, kanalın oluşturulduğu gibi, `Add` ve `Subtract` gibi yöntemlere sahip ancak `Close`değil, `ICalculator` arabirimi kullanılarak istemci uygulamada bildirildiği anlamına gelir. `Close` yöntemi <xref:System.ServiceModel.ICommunicationObject> arabirimini kaynak.

```csharp
// Close the channel.
 ((IClientChannel)client).Close();
```

Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemci uygulamasını kapatmak için istemci penceresinde ENTER tuşuna basın.

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin. Bu örneğin meta veri yayımlamayı etkinleştirmediğini unutmayın. İstemci türünü yeniden oluşturmak için önce Bu örnek için meta veri yayımlamayı etkinleştirmeniz gerekir.

3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.

### <a name="to-run-the-sample-cross-machine"></a>Örnek çapraz makineyi çalıştırmak için

1. Aşağıdaki kodda yer alan "localhost" değerini hizmeti çalıştıran makinenin tam adı ile değiştirin.

    ```csharp
    EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");
    ```

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ChannelFactory`
