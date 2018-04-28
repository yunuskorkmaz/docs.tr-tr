---
title: Özel Bağlama Kesinliği
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e13bf96-5de0-4476-b646-5f150774418d
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 44bedc3290d9c10078806ed63a8c5ddfe9754801
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="custom-binding-imperative"></a><span data-ttu-id="86e4e-102">Özel Bağlama Kesinliği</span><span class="sxs-lookup"><span data-stu-id="86e4e-102">Custom Binding Imperative</span></span>
<span data-ttu-id="86e4e-103">Örnek tanımlamak ve bir yapılandırma dosyası kullanmadan özel bağlama kullanma kesinlik temelli kodunun nasıl yazılacağını gösterir veya [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] istemci oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="86e4e-103">The sample demonstrates how to write imperative code to define and use custom bindings without using a configuration file or a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] generated client.</span></span> <span data-ttu-id="86e4e-104">Bu örnek HTTP taşıma ve güvenilir bir HTTP tabanlı bağlama oluşturmak için güvenilir oturum kanalı tarafından sağlanan özellikleri birleştirir.</span><span class="sxs-lookup"><span data-stu-id="86e4e-104">This sample combines the features provided by the HTTP transport and the reliable session channel to create a reliable HTTP-based binding.</span></span> <span data-ttu-id="86e4e-105">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesap makinesi hizmetinin uygular.</span><span class="sxs-lookup"><span data-stu-id="86e4e-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="86e4e-106">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="86e4e-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="86e4e-107">Hem istemci hem de hizmet özel bağlama iki bağlama öğeleri (güvenilir oturum ve HTTP) içeren oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="86e4e-107">On both the client and the service, a custom binding is created that contains two binding elements (Reliable Session and HTTP):</span></span>  

```csharp
ReliableSessionBindingElement reliableSession = new ReliableSessionBindingElement();  
reliableSession.Ordered = true;  
  
HttpTransportBindingElement httpTransport = new HttpTransportBindingElement();  
httpTransport.AuthenticationScheme = System.Net.AuthenticationSchemes.Anonymous;  
httpTransport.HostNameComparisonMode = HostNameComparisonMode.StrongWildcard;  
  
CustomBinding binding = new CustomBinding(reliableSession, httpTransport);  
```
  
 <span data-ttu-id="86e4e-108">Hizmette bağlama ServiceHost için bir uç nokta ekleyerek kullanılır:</span><span class="sxs-lookup"><span data-stu-id="86e4e-108">On the service, the binding is used by adding an endpoint to the ServiceHost:</span></span>  

```csharp
serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, "");  
```

 <span data-ttu-id="86e4e-109">İstemcide, bağlama tarafından kullanılan bir <xref:System.ServiceModel.ChannelFactory> hizmet bir kanal oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="86e4e-109">On the client, the binding is used by a <xref:System.ServiceModel.ChannelFactory> to create a channel to the service:</span></span>  

```csharp
EndpointAddress address = new EndpointAddress("http://localhost:8000/servicemodelsamples/service");  
ChannelFactory<ICalculator> channelFactory = new ChannelFactory<ICalculator>(binding, address);  
ICalculator channel = channelFactory.CreateChannel();  
```

 <span data-ttu-id="86e4e-110">Bu kanalın daha sonra hizmetiyle etkileşim kurmak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="86e4e-110">This channel is then used to interact with the service:</span></span>  

```csharp
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = channel.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```

 <span data-ttu-id="86e4e-111">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="86e4e-111">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="86e4e-112">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="86e4e-112">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="86e4e-113">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="86e4e-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="86e4e-114">Gerçekleştirilen mutlaka [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="86e4e-114">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="86e4e-115">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="86e4e-115">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="86e4e-116">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="86e4e-116">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="86e4e-117">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="86e4e-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="86e4e-118">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="86e4e-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="86e4e-119">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="86e4e-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="86e4e-120">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="86e4e-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Custom\Imperative`  
  
## <a name="see-also"></a><span data-ttu-id="86e4e-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="86e4e-121">See Also</span></span>  
 [<span data-ttu-id="86e4e-122">Özel Bağlama</span><span class="sxs-lookup"><span data-stu-id="86e4e-122">Custom Binding</span></span>](http://msdn.microsoft.com/library/657e8143-beb0-472d-9cfe-ed1a19c2ab08)
