---
title: Kesin
ms.date: 03/30/2017
ms.assetid: 4f7ce807-c0e4-407a-92a6-22abafb40b51
ms.openlocfilehash: b0a1b1dfca78a844364cfe977860915769980a04
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61990060"
---
# <a name="imperative"></a>Kesin

Bu örnek nasıl tanımlanacağını gösterir bir <xref:System.ServiceModel.WSHttpBinding> tanımlamak yerine kod kullanarak bir hizmet için `wsHttpBinding` yapılandırmasında bağlama. Bu örnek dayanır [Başlarken](getting-started-sample.md) hesaplayıcı hizmet uygulayan.

> [!NOTE]
> Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.

Aşağıdaki kod nasıl bir bağlama kodda kesin tanımlanacağını gösterir.

```csharp
public static void Main()
{
    WSHttpBinding binding = new WSHttpBinding();
    binding.Name = "binding1";
    binding.HostNameComparisonMode =
        HostNameComparisonMode.StrongWildcard;
    binding.Security.Mode = SecurityMode.Message;
    binding.ReliableSession.Enabled = false;
    binding.TransactionFlow = false;

    Uri baseAddress =
        new Uri("http://localhost:8000/servicemodelsamples/service");

    // Create a ServiceHost for the CalculatorService type and provide the base address.
    using(ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
    {
        serviceHost.AddServiceEndpoint(typeof(ICalculator), 
                                       binding, baseAddress);
        // Open the ServiceHostBase to create listeners and start listening for messages.
        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();
        // Close the ServiceHostBase to shutdown the service.
        serviceHost.Close();
    }
}
```

 İstemci aşağıdaki örnek kodda gösterildiği gibi hizmet ile iletişim kurmak için bir kanal oluşturur.

```csharp
WSHttpBinding binding = new WSHttpBinding();
binding.Name = "binding1";
binding.HostNameComparisonMode = HostNameComparisonMode.StrongWildcard;
binding.Security.Mode = SecurityMode.Message;
binding.ReliableSession.Enabled = false;
binding.TransactionFlow = false;

String url = "http://localhost:8000/servicemodelsamples/service";
EndpointAddress address = new EndpointAddress(url);
ChannelFactory<ICalculator> channelFactory = new ChannelFactory<ICalculator>(binding,address);
ICalculator channel = channelFactory.CreateChannel();
```

 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

## <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma

1. Gerçekleştirilen mutlaka [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](one-time-setup-procedure-for-the-wcf-samples.md).

2. Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](building-the-samples.md).

3. Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](running-the-samples.md).

> [!IMPORTANT]
> Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Imperative`