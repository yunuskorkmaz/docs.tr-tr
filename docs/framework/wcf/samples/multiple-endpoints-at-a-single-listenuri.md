---
title: "Bir ListenUri için Birden Fazla Belirteç"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 911ffad4-4d47-4430-b7c2-79192ce6bcbd
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 12d7d763f25fe27ce23cf57cfcfa9a23a47d85ef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="multiple-endpoints-at-a-single-listenuri"></a><span data-ttu-id="d36fc-102">Bir ListenUri için Birden Fazla Belirteç</span><span class="sxs-lookup"><span data-stu-id="d36fc-102">Multiple Endpoints at a Single ListenUri</span></span>
<span data-ttu-id="d36fc-103">Birden çok uç tek bir noktada barındıran bir hizmeti bu örnek gösteriyor `ListenUri`.</span><span class="sxs-lookup"><span data-stu-id="d36fc-103">This sample demonstrates a service that hosts multiple endpoints at a single `ListenUri`.</span></span> <span data-ttu-id="d36fc-104">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesap makinesi hizmetinin uygular.</span><span class="sxs-lookup"><span data-stu-id="d36fc-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d36fc-105">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="d36fc-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d36fc-106">Örnekte gösterildiği şekilde [birden çok uç nokta](../../../../docs/framework/wcf/samples/multiple-endpoints.md) örnek, bir hizmet birden çok uç nokta, her biri farklı adresleri ve büyük olasılıkla ayrıca farklı bağlamaları barındırabilir.</span><span class="sxs-lookup"><span data-stu-id="d36fc-106">As demonstrated in the [Multiple Endpoints](../../../../docs/framework/wcf/samples/multiple-endpoints.md) sample, a service can host multiple endpoints, each with different addresses and possibly also different bindings.</span></span> <span data-ttu-id="d36fc-107">Bu örnek aynı adresindeki birden fazla uç noktası ana bilgisayar mümkün olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d36fc-107">This sample shows that it is possible to host multiple endpoints at the same address.</span></span> <span data-ttu-id="d36fc-108">Bu örnek ayrıca bir hizmet uç noktası olan adresleri iki tür arasındaki farklar gösterilmektedir: `EndpointAddress` ve `ListenUri`.</span><span class="sxs-lookup"><span data-stu-id="d36fc-108">This sample also demonstrates the differences between the two kinds of addresses that a service endpoint has: `EndpointAddress` and `ListenUri`.</span></span>  
  
 <span data-ttu-id="d36fc-109">`EndpointAddress` Mantıksal bir hizmet adresidir.</span><span class="sxs-lookup"><span data-stu-id="d36fc-109">The `EndpointAddress` is the logical address of a service.</span></span> <span data-ttu-id="d36fc-110">SOAP iletilerine ele alınan adresidir.</span><span class="sxs-lookup"><span data-stu-id="d36fc-110">It is the address that SOAP messages are addressed to.</span></span> <span data-ttu-id="d36fc-111">`ListenUri` Fiziksel hizmet adresidir.</span><span class="sxs-lookup"><span data-stu-id="d36fc-111">The `ListenUri` is the physical address of the service.</span></span> <span data-ttu-id="d36fc-112">Bağlantı noktası ve adres bilgilerini nerede hizmet uç noktası gerçekten iletileri geçerli makineye bekler sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d36fc-112">It has the port and address information where the service endpoint actually listens for messages on the current machine.</span></span> <span data-ttu-id="d36fc-113">Çoğu durumda, farklı bu adresler için gerek yoktur; zaman bir `ListenUri` açıkça belirtilmediği takdirde URI'si için varsayılan olarak `EndpointAddress` bitiş noktası.</span><span class="sxs-lookup"><span data-stu-id="d36fc-113">In most cases, there is no need for these addresses to differ; when a `ListenUri` is not explicitly specified, it defaults to the URI of the `EndpointAddress` of the endpoint.</span></span> <span data-ttu-id="d36fc-114">Bazı durumlarda, bunları ne zaman iletileri kabul edebilir bir yönlendirici yapılandırma farklı Hizmetleri sayıya ele gibi ayırt etmek kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="d36fc-114">In a few cases, it is useful to distinguish them, such as when configuring a router, which might accept messages addressed to a number of different services.</span></span>  
  
## <a name="service"></a><span data-ttu-id="d36fc-115">Hizmet</span><span class="sxs-lookup"><span data-stu-id="d36fc-115">Service</span></span>  
 <span data-ttu-id="d36fc-116">Bu örnek hizmetinde iki sözleşmeleri sahip `ICalculator` ve `IEcho`.</span><span class="sxs-lookup"><span data-stu-id="d36fc-116">The service in this sample has two contracts, `ICalculator` and `IEcho`.</span></span> <span data-ttu-id="d36fc-117">Ek olarak her zamanki `IMetadataExchange` uç noktası, üç uygulama uç noktaları, aşağıdaki kodda gösterildiği gibi vardır.</span><span class="sxs-lookup"><span data-stu-id="d36fc-117">In addition to the customary `IMetadataExchange` endpoint, there are three application endpoints, as shown in the following code.</span></span>  
  
```xml  
<endpoint address="urn:Stuff"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.ICalculator"   
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
<endpoint address="urn:Stuff"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IEcho"   
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
<endpoint address="urn:OtherEcho"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IEcho"   
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
```  
  
 <span data-ttu-id="d36fc-118">Tüm üç bitiş noktaları aynı anda barındırılan `ListenUri` ve aynı `binding` -bitiş noktaları aynı `ListenUri` iletileri bu fiziksel adresindeki üzerinde dinleyen bir tek kanal yığını paylaşan olduğundan, aynı bağlama olması gerekir Makine.</span><span class="sxs-lookup"><span data-stu-id="d36fc-118">All three endpoints are hosted at the same `ListenUri` and use the same `binding` - endpoints at the same `ListenUri` must have the same binding, because they are sharing a single channel stack that listens for messages at that physical address on the machine.</span></span> <span data-ttu-id="d36fc-119">`address` Her uç noktasını URN; genellikle fiziksel konumlara adresleri temsil eden ancak adres eşleştirme ve bu örnekte gösterildiği gibi filtreleme amaçlı olarak kullanıldığından aslında adresi URI, her türlü olabilir.</span><span class="sxs-lookup"><span data-stu-id="d36fc-119">The `address` of each endpoint is a URN; though typically addresses represent physical locations, in fact the address can be any kind of URI, because the address is used for matching and filtering purposes as is demonstrated in this sample.</span></span>  
  
 <span data-ttu-id="d36fc-120">Tüm üç bitiş noktaları aynı paylaştığından `ListenUri`, ileti, geldiğinde [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ileti hedefleyen için hangi uç noktaya karar vermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d36fc-120">Because all three endpoints share the same `ListenUri`, when a message arrives there, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] must decide which endpoint the message is destined for.</span></span> <span data-ttu-id="d36fc-121">Her uç nokta iki bölümden oluşan bir ileti filtresi vardır: adresi filtresi ve sözleşme Filtresi.</span><span class="sxs-lookup"><span data-stu-id="d36fc-121">Each endpoint has a message filter that is comprised of two parts: the address filter and the contract filter.</span></span> <span data-ttu-id="d36fc-122">Adres filtre ile eşleşen `To` hizmet uç noktası adresine SOAP iletisi.</span><span class="sxs-lookup"><span data-stu-id="d36fc-122">The address filter matches the `To` of the SOAP message to the address of the service endpoint.</span></span> <span data-ttu-id="d36fc-123">Örneğin, yalnızca iletileri ele `To "Urn:OtherEcho"` bu hizmetin üçüncü uç noktası için bir aday değildir.</span><span class="sxs-lookup"><span data-stu-id="d36fc-123">For example, only messages addressed `To "Urn:OtherEcho"` are candidates for the third endpoint of this service.</span></span> <span data-ttu-id="d36fc-124">Sözleşme filtresi belirli bir sözleşme işlemlerle ilişkili eylemler eşleşir.</span><span class="sxs-lookup"><span data-stu-id="d36fc-124">The contract filter matches the Actions associated with the operations of a particular contract.</span></span> <span data-ttu-id="d36fc-125">Örneğin, eylemiyle iletileri `IEcho`.</span><span class="sxs-lookup"><span data-stu-id="d36fc-125">For example, messages with the action of `IEcho`.</span></span> <span data-ttu-id="d36fc-126">`Echo`çünkü ikinci ve üçüncü uç noktalar için bu hizmetin sözleşme filtrelerle eşleşen Bu uç noktaları konak her ikisi de `IEcho` sözleşme.</span><span class="sxs-lookup"><span data-stu-id="d36fc-126">`Echo` matches the contract filters of both the second and third endpoints of this service, because both of those endpoints host the `IEcho` contract.</span></span>  
  
 <span data-ttu-id="d36fc-127">Bu nedenle adresi filtresi ve sözleşme filtresi birleşimi, bu hizmetin ulaşan her ileti yolu mümkün kılar `ListenUri` doğru uç noktası.</span><span class="sxs-lookup"><span data-stu-id="d36fc-127">Thus the combination of address filter and contract filter makes it possible to route each message that arrives at this service's `ListenUri` to the correct endpoint.</span></span> <span data-ttu-id="d36fc-128">Diğer uç noktalarından farklı bir adresine gönderilen iletileri kabul ettiğinden üçüncü uç noktası diğer iki Ayrıştırılan.</span><span class="sxs-lookup"><span data-stu-id="d36fc-128">The third endpoint is differentiated from the other two because it accepts messages sent to a different address from the other endpoints.</span></span> <span data-ttu-id="d36fc-129">Birinci ve ikinci uç noktaları birbirinden sözleşmelerine (gelen ileti eylem) göre ayrılır.</span><span class="sxs-lookup"><span data-stu-id="d36fc-129">The first and second endpoints are differentiated from each other based on their contracts (the Action of the incoming message).</span></span>  
  
## <a name="client"></a><span data-ttu-id="d36fc-130">İstemci</span><span class="sxs-lookup"><span data-stu-id="d36fc-130">Client</span></span>  
 <span data-ttu-id="d36fc-131">Yalnızca iki farklı adresi uç sunucuda yüklü olduğu istemci uç noktalarını da iki adresine sahip.</span><span class="sxs-lookup"><span data-stu-id="d36fc-131">Just as endpoints on the server have two different addresses, client endpoints also have two addresses.</span></span> <span data-ttu-id="d36fc-132">Hem sunucu hem de istemci mantıksal adresi adlı `EndpointAddress`.</span><span class="sxs-lookup"><span data-stu-id="d36fc-132">On both server and client, the logical address is called the `EndpointAddress`.</span></span> <span data-ttu-id="d36fc-133">Ancak fiziksel adres adlı ancak `ListenUri` fiziksel adres sunucuda istemci adlı `Via`.</span><span class="sxs-lookup"><span data-stu-id="d36fc-133">But whereas the physical address is called the `ListenUri` on the server, on the client, the physical address is called the `Via`.</span></span>  
  
 <span data-ttu-id="d36fc-134">Sunucuda gibi varsayılan olarak, bu iki adres aynıdır.</span><span class="sxs-lookup"><span data-stu-id="d36fc-134">As on the server, by default, these two addresses are the same.</span></span> <span data-ttu-id="d36fc-135">Belirtmek için bir `Via` uç noktanın adresinden farklı istemci üzerinde `ClientViaBehavior` kullanılır:</span><span class="sxs-lookup"><span data-stu-id="d36fc-135">To specify a `Via` on the client that is different from the endpoint's address, `ClientViaBehavior` is used:</span></span>  
  
```  
Uri via = new Uri("http://localhost/ServiceModelSamples/service.svc");  
CalculatorClient calcClient = new CalculatorClient();  
calcClient.ChannelFactory.Endpoint.Behaviors.Add(  
        new ClientViaBehavior(via));  
```  
  
 <span data-ttu-id="d36fc-136">Her zamanki gibi adres Svcutil.exe tarafından oluşturulan istemci yapılandırma dosyasından birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="d36fc-136">As usual, the address comes from the client configuration file, which was generated by Svcutil.exe.</span></span> <span data-ttu-id="d36fc-137">`Via` (İçin karşılık geldiği `ListenUri` hizmetinin) hizmetin meta verilerde görünmez ve bu bilgileri istemci-bant (yalnızca gibi hizmetin meta veri adresi) için bildirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d36fc-137">The `Via` (which corresponds to the `ListenUri` of the service) does not appear in the service's metadata and so this information must be communicated to the client out-of-band (just like the service's metadata address).</span></span>  
  
 <span data-ttu-id="d36fc-138">Bu örnekte istemci iletileri gönderir her sunucunun üç uygulama uç noktaları için onun göstermek için ile iletişim kurabilmesini (ve ayırt) tüm üç uç noktaları, hepsi aynı olsa bile `Via`.</span><span class="sxs-lookup"><span data-stu-id="d36fc-138">The client in this sample sends messages to each of the server's three application endpoints, to demonstrate that it can communicate with (and differentiate) all three endpoints, even though they all have the same `Via`.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d36fc-139">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="d36fc-139">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d36fc-140">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d36fc-140">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="d36fc-141">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d36fc-141">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="d36fc-142">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d36fc-142">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d36fc-143">Çapraz-makine için Client.cs dosyasındaki localhost hizmeti makine adı ile değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d36fc-143">For cross-machine, you must replace localhost in the Client.cs file with the name of the service machine.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d36fc-144">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="d36fc-144">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d36fc-145">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d36fc-145">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d36fc-146">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="d36fc-146">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d36fc-147">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d36fc-147">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpointsSingleUri`  
  
## <a name="see-also"></a><span data-ttu-id="d36fc-148">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d36fc-148">See Also</span></span>
