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
# <a name="channel-factory"></a><span data-ttu-id="f5e85-102">Kanal Fabrikası</span><span class="sxs-lookup"><span data-stu-id="f5e85-102">Channel Factory</span></span>
<span data-ttu-id="f5e85-103">Bu örnek bir istemci uygulaması bir kanal ile nasıl oluşturabileceğinizi gösterir <xref:System.ServiceModel.ChannelFactory> oluşturulan bir istemci yerine sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f5e85-103">This sample demonstrates how a client application can create a channel with the <xref:System.ServiceModel.ChannelFactory> class instead of a generated client.</span></span> <span data-ttu-id="f5e85-104">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesap makinesi hizmetinin uygular.</span><span class="sxs-lookup"><span data-stu-id="f5e85-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f5e85-105">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="f5e85-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f5e85-106">Bu örnekte <xref:System.ServiceModel.ChannelFactory%601> hizmet uç noktası için bir kanal oluşturmak için sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f5e85-106">This sample uses the <xref:System.ServiceModel.ChannelFactory%601> class to create a channel to a service endpoint.</span></span> <span data-ttu-id="f5e85-107">Genellikle, bir hizmet uç noktası için bir kanal oluşturmak için bir istemci türü ile oluşturduğunuz [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ve oluşturulan türünün bir örneği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f5e85-107">Typically, to create a channel to a service endpoint you generate a client type with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) and create an instance of the generated type.</span></span> <span data-ttu-id="f5e85-108">Kullanarak bir kanal oluşturabilirsiniz <xref:System.ServiceModel.ChannelFactory%601> Bu örnekte gösterildiği gibi sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f5e85-108">You can also create a channel by using the <xref:System.ServiceModel.ChannelFactory%601> class, as demonstrated in this sample.</span></span> <span data-ttu-id="f5e85-109">Aşağıdaki örnek kod tarafından oluşturulan hizmet ile hizmeti aynı [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="f5e85-109">The service created by the following sample code is identical to the service in the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
```  
EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
WSHttpBinding binding = new WSHttpBinding();  
ChannelFactory<ICalculator> factory = new   
                    ChannelFactory<ICalculator>(binding, address);  
ICalculator channel = factory.CreateChannel();  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="f5e85-110">Bu örnek bir makineler arası senaryosunda çalıştırıyorsanız, önceki kod "localhost" hizmetini çalıştıran bilgisayarın tam adı ile değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f5e85-110">If you are running this sample in a cross-machine scenario, you must replace "localhost" in the preceding code with the fully-qualified name of the machine that is running the service.</span></span> <span data-ttu-id="f5e85-111">Bu örnek, bu kodda yapılmalıdır için uç nokta adresi ayarlamak için yapılandırma kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="f5e85-111">This sample does not use configuration to set the endpoint address, so this must be done in code.</span></span>  
  
 <span data-ttu-id="f5e85-112">Kanalı oluşturduktan sonra hizmet işlemleri yalnızca olarak oluşturulan bir istemci ile çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="f5e85-112">Once the channel is created, service operations can be invoked just as with a generated client.</span></span>  
  
```  
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = channel.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```  
  
 <span data-ttu-id="f5e85-113">Kanal kapatmak için öncelikle için dönüştürülmelidir bir <xref:System.ServiceModel.IClientChannel> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="f5e85-113">To close the channel, it must first be cast to an <xref:System.ServiceModel.IClientChannel> interface.</span></span> <span data-ttu-id="f5e85-114">Oluşturulan kanalı kullanılarak istemci uygulama bildirildiğinden budur `ICalculator` yöntemlerine sahiptir arabirimi gibi `Add` ve `Subtract` ama `Close`.</span><span class="sxs-lookup"><span data-stu-id="f5e85-114">This is because the channel as generated is declared in the client application using the `ICalculator` interface, which has methods like `Add` and `Subtract` but not `Close`.</span></span> <span data-ttu-id="f5e85-115">`Close` Yöntemi kaynaklandığı <xref:System.ServiceModel.ICommunicationObject> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="f5e85-115">The `Close` method originates on the <xref:System.ServiceModel.ICommunicationObject> interface.</span></span>  
  
```  
// Close the channel.  
 ((IClientChannel)client).Close();  
```  
  
 <span data-ttu-id="f5e85-116">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f5e85-116">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="f5e85-117">İstemci uygulamayı kapatın İstemcisi penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="f5e85-117">Press ENTER in the client window to shut down the client application.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f5e85-118">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="f5e85-118">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f5e85-119">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f5e85-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="f5e85-120">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f5e85-120">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span> <span data-ttu-id="f5e85-121">Bu örnek meta veri yayımlama etkinleştirmez unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f5e85-121">Note that this sample does not enable metadata publishing.</span></span> <span data-ttu-id="f5e85-122">Meta veri yayımlama istemci türü yeniden oluşturmak için bu örnek için önce etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f5e85-122">You must first enable metadata publishing for this sample to regenerate the client type.</span></span>  
  
3.  <span data-ttu-id="f5e85-123">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f5e85-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-cross-machine"></a><span data-ttu-id="f5e85-124">Örneği çalıştırmak için makine arası</span><span class="sxs-lookup"><span data-stu-id="f5e85-124">To run the sample cross machine</span></span>  
  
1.  <span data-ttu-id="f5e85-125">Aşağıdaki kodda "localhost" hizmetini çalıştıran bilgisayarın tam adı ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f5e85-125">Replace "localhost" in the following code with the fully-qualified name of the machine that is running the service.</span></span>  
  
    ```  
    EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
    ```  
  
> [!IMPORTANT]
>  <span data-ttu-id="f5e85-126">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="f5e85-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f5e85-127">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="f5e85-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f5e85-128">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="f5e85-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f5e85-129">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="f5e85-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ChannelFactory`  
  
## <a name="see-also"></a><span data-ttu-id="f5e85-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f5e85-130">See Also</span></span>
