---
title: Kesin
ms.date: 03/30/2017
ms.assetid: 4f7ce807-c0e4-407a-92a6-22abafb40b51
ms.openlocfilehash: cb8cd0814c695f0f870b7b160ca99e411724d302
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677660"
---
# <a name="imperative"></a><span data-ttu-id="a9623-102">Kesin</span><span class="sxs-lookup"><span data-stu-id="a9623-102">Imperative</span></span>
<span data-ttu-id="a9623-103">Bu örnek nasıl tanımlanacağını gösterir bir <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> tanımlama yerine kod kullanarak bir hizmet için `wsHttpBinding` yapılandırmasında bağlama.</span><span class="sxs-lookup"><span data-stu-id="a9623-103">This sample demonstrates how to define a <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> for a service using code, instead of defining the `wsHttpBinding` binding in configuration.</span></span> <span data-ttu-id="a9623-104">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesaplayıcı hizmet uygulayan.</span><span class="sxs-lookup"><span data-stu-id="a9623-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a9623-105">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="a9623-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a9623-106">Aşağıdaki kod nasıl bir bağlama kodda kesin tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a9623-106">The following code demonstrates how to define a binding imperatively in code.</span></span>  
  
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
  
 <span data-ttu-id="a9623-107">İstemci aşağıdaki örnek kodda gösterildiği gibi hizmet ile iletişim kurmak için bir kanal oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a9623-107">The client creates a channel to communicate with the service as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="a9623-108">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a9623-108">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="a9623-109">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a9623-109">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a9623-110">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="a9623-110">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a9623-111">Gerçekleştirilen mutlaka [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a9623-111">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="a9623-112">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a9623-112">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="a9623-113">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a9623-113">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a9623-114">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="a9623-114">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a9623-115">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a9623-115">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a9623-116">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="a9623-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a9623-117">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="a9623-117">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Imperative`  
  
## <a name="see-also"></a><span data-ttu-id="a9623-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9623-118">See also</span></span>
