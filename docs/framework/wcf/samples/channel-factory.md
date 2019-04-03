---
title: Kanal Fabrikası
ms.date: 03/30/2017
ms.assetid: 09b53aa1-b13c-476c-a461-e82fcacd2a8b
ms.openlocfilehash: dd95417ba084e69bc14ce3380a57d44fd8dd3e88
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819612"
---
# <a name="channel-factory"></a><span data-ttu-id="40d7d-102">Kanal Fabrikası</span><span class="sxs-lookup"><span data-stu-id="40d7d-102">Channel Factory</span></span>
<span data-ttu-id="40d7d-103">Bu örnek, bir istemci uygulaması ile bir kanalı nasıl oluşturacağınızı gösterir. <xref:System.ServiceModel.ChannelFactory> yerine oluşturulmuş istemci sınıfı.</span><span class="sxs-lookup"><span data-stu-id="40d7d-103">This sample demonstrates how a client application can create a channel with the <xref:System.ServiceModel.ChannelFactory> class instead of a generated client.</span></span> <span data-ttu-id="40d7d-104">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesaplayıcı hizmet uygulayan.</span><span class="sxs-lookup"><span data-stu-id="40d7d-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="40d7d-105">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="40d7d-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="40d7d-106">Bu örnekte <xref:System.ServiceModel.ChannelFactory%601> hizmet uç noktası için bir kanal oluşturmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="40d7d-106">This sample uses the <xref:System.ServiceModel.ChannelFactory%601> class to create a channel to a service endpoint.</span></span> <span data-ttu-id="40d7d-107">Genellikle, bir hizmet uç noktası için bir kanal oluşturmak için bir istemci türü ile oluşturduğunuz [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ve oluşturulan türün bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="40d7d-107">Typically, to create a channel to a service endpoint you generate a client type with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) and create an instance of the generated type.</span></span> <span data-ttu-id="40d7d-108">Kullanarak bir kanalı oluşturabilirsiniz <xref:System.ServiceModel.ChannelFactory%601> , bu örnekte gösterildiği gibi sınıf.</span><span class="sxs-lookup"><span data-stu-id="40d7d-108">You can also create a channel by using the <xref:System.ServiceModel.ChannelFactory%601> class, as demonstrated in this sample.</span></span> <span data-ttu-id="40d7d-109">Aşağıdaki örnek kod tarafından oluşturulan hizmet hizmette aynı [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="40d7d-109">The service created by the following sample code is identical to the service in the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
```csharp  
EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
WSHttpBinding binding = new WSHttpBinding();  
ChannelFactory<ICalculator> factory = new   
                    ChannelFactory<ICalculator>(binding, address);  
ICalculator channel = factory.CreateChannel();  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="40d7d-110">Bu örnek bir çapraz makine senaryosunda çalıştırıyorsanız, önceki kodda, "localhost" hizmetini çalıştıran makinenin tam adıyla değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="40d7d-110">If you are running this sample in a cross-machine scenario, you must replace "localhost" in the preceding code with the fully-qualified name of the machine that is running the service.</span></span> <span data-ttu-id="40d7d-111">Bu örnek, bu kod yapılmalıdır için uç nokta adresi ayarlamak için yapılandırma kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="40d7d-111">This sample does not use configuration to set the endpoint address, so this must be done in code.</span></span>  
  
 <span data-ttu-id="40d7d-112">Kanal oluşturulduktan sonra hizmet işlemleri ile oluşturulan bir istemci olarak çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="40d7d-112">Once the channel is created, service operations can be invoked just as with a generated client.</span></span>  
  
```csharp  
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = channel.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```  
  
 <span data-ttu-id="40d7d-113">Kanal kapatmak için önce için dönüştürülmelidir bir <xref:System.ServiceModel.IClientChannel> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="40d7d-113">To close the channel, it must first be cast to an <xref:System.ServiceModel.IClientChannel> interface.</span></span> <span data-ttu-id="40d7d-114">Oluşturulan kanal istemcisi kullanılarak uygulama bildirilmiş olmasıdır `ICalculator` yöntemleri olan arabirimi gibi `Add` ve `Subtract` ama `Close`.</span><span class="sxs-lookup"><span data-stu-id="40d7d-114">This is because the channel as generated is declared in the client application using the `ICalculator` interface, which has methods like `Add` and `Subtract` but not `Close`.</span></span> <span data-ttu-id="40d7d-115">`Close` Yöntemi kaynaklanan üzerinde <xref:System.ServiceModel.ICommunicationObject> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="40d7d-115">The `Close` method originates on the <xref:System.ServiceModel.ICommunicationObject> interface.</span></span>  
  
```csharp  
// Close the channel.  
 ((IClientChannel)client).Close();  
```  
  
 <span data-ttu-id="40d7d-116">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="40d7d-116">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="40d7d-117">İstemci uygulamayı kapatın istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="40d7d-117">Press ENTER in the client window to shut down the client application.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="40d7d-118">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="40d7d-118">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="40d7d-119">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="40d7d-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="40d7d-120">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="40d7d-120">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span> <span data-ttu-id="40d7d-121">Bu örnek meta veri yayımlama etkinleştirmez unutmayın.</span><span class="sxs-lookup"><span data-stu-id="40d7d-121">Note that this sample does not enable metadata publishing.</span></span> <span data-ttu-id="40d7d-122">Meta veri yayımlama istemci türünü yeniden oluşturmak Bu örnek için önce etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="40d7d-122">You must first enable metadata publishing for this sample to regenerate the client type.</span></span>  
  
3.  <span data-ttu-id="40d7d-123">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="40d7d-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-cross-machine"></a><span data-ttu-id="40d7d-124">Örneği çalıştırmak için makine çapraz</span><span class="sxs-lookup"><span data-stu-id="40d7d-124">To run the sample cross machine</span></span>  
  
1.  <span data-ttu-id="40d7d-125">Aşağıdaki kodda "localhost" hizmetini çalıştıran makinenin tam adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="40d7d-125">Replace "localhost" in the following code with the fully-qualified name of the machine that is running the service.</span></span>  
  
    ```csharp  
    EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
    ```  
  
> [!IMPORTANT]
>  <span data-ttu-id="40d7d-126">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="40d7d-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="40d7d-127">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="40d7d-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="40d7d-128">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="40d7d-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="40d7d-129">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="40d7d-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ChannelFactory`  
  
