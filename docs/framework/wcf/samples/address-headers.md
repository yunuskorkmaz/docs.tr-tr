---
title: "Adres Üstbilgileri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0c94d4a-3bde-4b4d-bb6d-9f12bc3a6940
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8d46dac29157455f736e30515f4bc6b277b63694
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="address-headers"></a><span data-ttu-id="d5925-102">Adres Üstbilgileri</span><span class="sxs-lookup"><span data-stu-id="d5925-102">Address Headers</span></span>
<span data-ttu-id="d5925-103">Adres üstbilgileri örneği kullanarak bir hizmet istemcilerin başvuru parametreleri nasıl geçirebilirsiniz gösterir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d5925-103">The Address Headers sample demonstrates how clients can pass reference parameters to a service using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5925-104">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="d5925-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d5925-105">WS-adresleme belirtimi bir uç nokta başvuru kavramı belirli bir Web Hizmeti uç noktası adresi için bir yol olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d5925-105">The WS-Addressing specification defines the notion of an endpoint reference as a way to address a particular Web service endpoint.</span></span> <span data-ttu-id="d5925-106">İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], uç nokta başvuruları Modellenen kullanarak `EndpointAddress` sınıfı - `EndpointAddress` adres alanının türü `ServiceEndpoint` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d5925-106">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], endpoint references are modeled using the `EndpointAddress` class - `EndpointAddress` is the type of the Address field of the `ServiceEndpoint` class.</span></span>  
  
 <span data-ttu-id="d5925-107">Uç nokta başvuru modeli her başvuru fazladan tanımlama bilgilerini eklemek bazı başvuru parametreleri taşıyabilir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="d5925-107">Part of the endpoint reference model is that each reference can carry some reference parameters that add extra identifying information.</span></span> <span data-ttu-id="d5925-108">İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], bu başvuru parametreleri örnekleri olarak Modellenen `AddressHeader` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d5925-108">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], these reference parameters are modeled as instances of `AddressHeader` class.</span></span>  
  
 <span data-ttu-id="d5925-109">Bu örnekte, istemci başvuru parametresi ekler `EndpointAddress` istemci uç noktası.</span><span class="sxs-lookup"><span data-stu-id="d5925-109">In this sample, the client adds a reference parameter to the `EndpointAddress` of the client endpoint.</span></span> <span data-ttu-id="d5925-110">Hizmet için bu başvuru parametresi arar ve onun "Hello" hizmet işlemi mantığında değerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d5925-110">The service looks for this reference parameter and uses its value in the logic of its "Hello" service operation.</span></span>  
  
## <a name="client"></a><span data-ttu-id="d5925-111">İstemci</span><span class="sxs-lookup"><span data-stu-id="d5925-111">Client</span></span>  
 <span data-ttu-id="d5925-112">İstemcinin bir başvuru parametre göndermek, onu eklemelisiniz bir `AddressHeader` için `EndpointAddress` , `ServiceEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="d5925-112">For the client to send a reference parameter, it must add an `AddressHeader` to the `EndpointAddress` of the `ServiceEndpoint`.</span></span> <span data-ttu-id="d5925-113">Çünkü `EndpointAddress` sınıfı değişmez, bir uç nokta adresi değiştirilmesini yapılmalıdır kullanarak `EndpointAddressBuilder` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d5925-113">Because the `EndpointAddress` class is immutable, modification of an endpoint address must be done using the `EndpointAddressBuilder` class.</span></span> <span data-ttu-id="d5925-114">Aşağıdaki kod, ileti bir parçası olarak bir başvuru parametre göndermek için istemci başlatır.</span><span class="sxs-lookup"><span data-stu-id="d5925-114">The following code initializes the client to send a reference parameter as part of its message.</span></span>  
  
```  
HelloClient client = new HelloClient();  
EndpointAddressBuilder builder =   
    new EndpointAddressBuilder(client.Endpoint.Address);  
AddressHeader header =   
    AddressHeader.CreateAddressHeader(IDName, IDNamespace, "John");  
builder.Headers.Add(header);  
client.Endpoint.Address = builder.ToEndpointAddress();  
```  
  
 <span data-ttu-id="d5925-115">Kod oluşturur bir `EndpointAddressBuilder` özgün kullanarak `EndpointAddress` başlangıç değeri olarak.</span><span class="sxs-lookup"><span data-stu-id="d5925-115">The code creates an `EndpointAddressBuilder` using the original `EndpointAddress` as an initial value.</span></span> <span data-ttu-id="d5925-116">Ardından, yeni oluşturulan adres üstbilgisi ekler; çağrı `CreateAddressHeadercreates` belirli ad, ad ve değere sahip bir üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="d5925-116">It then adds a newly created address header; the call to `CreateAddressHeadercreates` a header with a particular name, namespace, and value.</span></span> <span data-ttu-id="d5925-117">Burada "John" değeridir.</span><span class="sxs-lookup"><span data-stu-id="d5925-117">Here the value is "John".</span></span> <span data-ttu-id="d5925-118">Üstbilgi oluşturucuya eklendikten sonra `ToEndpointAddress()` yöntemi (değişebilir) oluşturucu geri istemci uç noktanın bir adres alanına atanan geri bir (değişmez) uç noktası adresi dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="d5925-118">Once the header is added to the builder, the `ToEndpointAddress()` method converts the (mutable) builder back into an (immutable) endpoint address, which is assigned back to the client endpoint's Address field.</span></span>  
  
 <span data-ttu-id="d5925-119">Şimdi istemci çağırdığında `Console.WriteLine(client.Hello());`, istemci elde edilen çıktıda görüldüğü şekilde hizmet bu adresi parametresinin değerini alabilir.</span><span class="sxs-lookup"><span data-stu-id="d5925-119">Now when the client calls `Console.WriteLine(client.Hello());`, the service is able to get the value of this address parameter, as seen in the resulting output of the client.</span></span>  
  
 `Hello, John`  
  
## <a name="server"></a><span data-ttu-id="d5925-120">Sunucu</span><span class="sxs-lookup"><span data-stu-id="d5925-120">Server</span></span>  
 <span data-ttu-id="d5925-121">Hizmet işlemi uygulama `Hello()` geçerli kullanan `OperationContext` gelen ileti üstbilgilerinde değerlerini incelemek için.</span><span class="sxs-lookup"><span data-stu-id="d5925-121">The implementation of the service operation `Hello()` uses the current `OperationContext` to inspect the values of the headers on the incoming message.</span></span>  
  
```  
string id = null;  
// look at headers on incoming message  
for (int i = 0;   
     i < OperationContext.Current.IncomingMessageHeaders.Count;   
     ++i)  
{  
    MessageHeaderInfo h =   
        OperationContext.Current.IncomingMessageHeaders[i];  
    // for any reference parameters with the correct name & namespace  
    if (h.IsReferenceParameter &&   
        h.Name == IDName &&   
        h.Namespace == IDNamespace)  
    {  
        // read the value of that header  
        XmlReader xr =   
OperationContext.Current.IncomingMessageHeaders.GetReaderAtHeader(i);  
        id = xr.ReadElementContentAsString();  
    }  
}  
return "Hello, " + id;  
```  
  
 <span data-ttu-id="d5925-122">Başvuru parametreleri belirli adla üstbilgileri arayan gelen ileti üzerinde tüm üstbilgileri üzerinden kodu tekrarlanan ve.</span><span class="sxs-lookup"><span data-stu-id="d5925-122">The code iterates over all the headers on the incoming message, looking for headers that are reference parameters with the particular name and.</span></span> <span data-ttu-id="d5925-123">Parametresi bulunduğunda parametresinin değeri okur ve "id" değişkeninde depolar.</span><span class="sxs-lookup"><span data-stu-id="d5925-123">When the parameter is found, it reads the value of the parameter and stores it in the "id" variable.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d5925-124">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="d5925-124">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d5925-125">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d5925-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="d5925-126">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d5925-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="d5925-127">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d5925-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d5925-128">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="d5925-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d5925-129">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d5925-129">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d5925-130">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="d5925-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d5925-131">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d5925-131">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\AddressHeaders`  
  
## <a name="see-also"></a><span data-ttu-id="d5925-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d5925-132">See Also</span></span>
