---
title: Kanal Fabrikası
ms.date: 03/30/2017
ms.assetid: 09b53aa1-b13c-476c-a461-e82fcacd2a8b
ms.openlocfilehash: 2aa44c4ef274fa548d490b0d8a648457a7b1e03b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600665"
---
# <a name="channel-factory"></a><span data-ttu-id="c4a64-102">Kanal Fabrikası</span><span class="sxs-lookup"><span data-stu-id="c4a64-102">Channel Factory</span></span>

<span data-ttu-id="c4a64-103">Bu örnek, bir istemci uygulamanın <xref:System.ServiceModel.ChannelFactory> oluşturulan istemci yerine sınıfı ile bir kanal nasıl oluşturacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="c4a64-103">This sample demonstrates how a client application can create a channel with the <xref:System.ServiceModel.ChannelFactory> class instead of a generated client.</span></span> <span data-ttu-id="c4a64-104">Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](getting-started-sample.md) Başlarken hizmetini temel alır.</span><span class="sxs-lookup"><span data-stu-id="c4a64-104">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span>

> [!NOTE]
> <span data-ttu-id="c4a64-105">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="c4a64-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="c4a64-106">Bu örnek, <xref:System.ServiceModel.ChannelFactory%601> bir hizmet uç noktasına kanal oluşturmak için sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="c4a64-106">This sample uses the <xref:System.ServiceModel.ChannelFactory%601> class to create a channel to a service endpoint.</span></span> <span data-ttu-id="c4a64-107">Genellikle, bir hizmet uç noktasına kanal oluşturmak için, [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) ile bir istemci türü oluşturun ve oluşturulan türün bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c4a64-107">Typically, to create a channel to a service endpoint you generate a client type with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) and create an instance of the generated type.</span></span> <span data-ttu-id="c4a64-108">Ayrıca <xref:System.ServiceModel.ChannelFactory%601> , bu örnekte gösterildiği gibi sınıfını kullanarak bir kanal oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4a64-108">You can also create a channel by using the <xref:System.ServiceModel.ChannelFactory%601> class, as demonstrated in this sample.</span></span> <span data-ttu-id="c4a64-109">Aşağıdaki örnek kod tarafından oluşturulan hizmet, [Başlarken](getting-started-sample.md)hizmeti ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="c4a64-109">The service created by the following sample code is identical to the service in the [Getting Started](getting-started-sample.md).</span></span>

```csharp
EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");
WSHttpBinding binding = new WSHttpBinding();
ChannelFactory<ICalculator> factory = new
                    ChannelFactory<ICalculator>(binding, address);
ICalculator channel = factory.CreateChannel();
```

> [!IMPORTANT]
> <span data-ttu-id="c4a64-110">Bu örneği bir çapraz makine senaryosunda çalıştırıyorsanız, yukarıdaki koddaki "localhost" hizmetini hizmeti çalıştıran makinenin tam adı ile değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="c4a64-110">If you are running this sample in a cross-machine scenario, you must replace "localhost" in the preceding code with the fully-qualified name of the machine that is running the service.</span></span> <span data-ttu-id="c4a64-111">Bu örnek, uç nokta adresini ayarlamak için yapılandırma kullanmaz, bu nedenle bu işlem kodda yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c4a64-111">This sample does not use configuration to set the endpoint address, so this must be done in code.</span></span>

<span data-ttu-id="c4a64-112">Kanal oluşturulduktan sonra, hizmet işlemleri, oluşturulan bir istemcide olduğu gibi çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="c4a64-112">Once the channel is created, service operations can be invoked just as with a generated client.</span></span>

```csharp
// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = channel.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
```

<span data-ttu-id="c4a64-113">Kanalı kapatmak için öncelikle bir arabirime dönüştürülmesi gerekir <xref:System.ServiceModel.IClientChannel> .</span><span class="sxs-lookup"><span data-stu-id="c4a64-113">To close the channel, it must first be cast to an <xref:System.ServiceModel.IClientChannel> interface.</span></span> <span data-ttu-id="c4a64-114">Bunun nedeni, kanalın oluşturulduğu gibi, `ICalculator` ve gibi yöntemlere sahip olan arabirimini kullanarak istemci uygulamasında bildirildiği anlamına gelir `Add` `Subtract` `Close` .</span><span class="sxs-lookup"><span data-stu-id="c4a64-114">This is because the channel as generated is declared in the client application using the `ICalculator` interface, which has methods like `Add` and `Subtract` but not `Close`.</span></span> <span data-ttu-id="c4a64-115">`Close`Yöntemi <xref:System.ServiceModel.ICommunicationObject> arayüzden kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="c4a64-115">The `Close` method originates on the <xref:System.ServiceModel.ICommunicationObject> interface.</span></span>

```csharp
// Close the channel.
 ((IClientChannel)client).Close();
```

<span data-ttu-id="c4a64-116">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c4a64-116">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="c4a64-117">İstemci uygulamasını kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c4a64-117">Press ENTER in the client window to shut down the client application.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c4a64-118">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="c4a64-118">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="c4a64-119">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="c4a64-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="c4a64-120">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="c4a64-120">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span> <span data-ttu-id="c4a64-121">Bu örneğin meta veri yayımlamayı etkinleştirmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c4a64-121">Note that this sample does not enable metadata publishing.</span></span> <span data-ttu-id="c4a64-122">İstemci türünü yeniden oluşturmak için önce Bu örnek için meta veri yayımlamayı etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c4a64-122">You must first enable metadata publishing for this sample to regenerate the client type.</span></span>

3. <span data-ttu-id="c4a64-123">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="c4a64-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

### <a name="to-run-the-sample-cross-machine"></a><span data-ttu-id="c4a64-124">Örnek çapraz makineyi çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="c4a64-124">To run the sample cross machine</span></span>

1. <span data-ttu-id="c4a64-125">Aşağıdaki kodda yer alan "localhost" değerini hizmeti çalıştıran makinenin tam adı ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c4a64-125">Replace "localhost" in the following code with the fully-qualified name of the machine that is running the service.</span></span>

    ```csharp
    EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");
    ```

> [!IMPORTANT]
> <span data-ttu-id="c4a64-126">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="c4a64-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c4a64-127">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c4a64-127">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="c4a64-128">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c4a64-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c4a64-129">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c4a64-129">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ChannelFactory`
