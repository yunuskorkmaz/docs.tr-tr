---
title: Adres Üstbilgileri
ms.date: 03/30/2017
ms.assetid: b0c94d4a-3bde-4b4d-bb6d-9f12bc3a6940
ms.openlocfilehash: 3bc8512fb2492a7249c81fc33a3c7b83904f1ccd
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715222"
---
# <a name="address-headers"></a><span data-ttu-id="e051b-102">Adres Üstbilgileri</span><span class="sxs-lookup"><span data-stu-id="e051b-102">Address Headers</span></span>

<span data-ttu-id="e051b-103">Adres üstbilgileri örneği, istemcilerin Windows Communication Foundation (WCF) kullanarak başvuru parametrelerini bir hizmete nasıl geçirebileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="e051b-103">The Address Headers sample demonstrates how clients can pass reference parameters to a service using Windows Communication Foundation (WCF).</span></span>

> [!NOTE]
> <span data-ttu-id="e051b-104">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="e051b-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="e051b-105">WS-Addressing belirtimi, belirli bir Web hizmeti uç noktasını ele almanın bir yolu olarak bir uç nokta başvurusunun kavramını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e051b-105">The WS-Addressing specification defines the notion of an endpoint reference as a way to address a particular Web service endpoint.</span></span> <span data-ttu-id="e051b-106">WCF 'de, uç nokta başvuruları `EndpointAddress` sınıfı kullanılarak modellenir-`EndpointAddress`, `ServiceEndpoint` sınıfının adres alanının türüdür.</span><span class="sxs-lookup"><span data-stu-id="e051b-106">In WCF, endpoint references are modeled using the `EndpointAddress` class - `EndpointAddress` is the type of the Address field of the `ServiceEndpoint` class.</span></span>

<span data-ttu-id="e051b-107">Uç nokta başvuru modelinin bir bölümü, her başvurunun ek tanımlayıcı bilgi ekleyen bazı başvuru parametrelerini taşıyacağından oluşur.</span><span class="sxs-lookup"><span data-stu-id="e051b-107">Part of the endpoint reference model is that each reference can carry some reference parameters that add extra identifying information.</span></span> <span data-ttu-id="e051b-108">WCF 'de, bu başvuru parametreleri `AddressHeader` sınıfının örnekleri olarak modellenir.</span><span class="sxs-lookup"><span data-stu-id="e051b-108">In WCF, these reference parameters are modeled as instances of `AddressHeader` class.</span></span>

<span data-ttu-id="e051b-109">Bu örnekte istemci, istemci uç noktasının `EndpointAddress` bir başvuru parametresi ekler.</span><span class="sxs-lookup"><span data-stu-id="e051b-109">In this sample, the client adds a reference parameter to the `EndpointAddress` of the client endpoint.</span></span> <span data-ttu-id="e051b-110">Hizmet bu başvuru parametresini arar ve "Hello" hizmet işleminin mantığındaki değerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e051b-110">The service looks for this reference parameter and uses its value in the logic of its "Hello" service operation.</span></span>

## <a name="client"></a><span data-ttu-id="e051b-111">İstemci</span><span class="sxs-lookup"><span data-stu-id="e051b-111">Client</span></span>

<span data-ttu-id="e051b-112">İstemcinin başvuru parametresi gönderebilmesi için, `ServiceEndpoint``EndpointAddress` bir `AddressHeader` eklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e051b-112">For the client to send a reference parameter, it must add an `AddressHeader` to the `EndpointAddress` of the `ServiceEndpoint`.</span></span> <span data-ttu-id="e051b-113">`EndpointAddress` sınıfı sabit olduğundan, bir uç nokta adresinin değiştirilmesi `EndpointAddressBuilder` sınıfı kullanılarak yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e051b-113">Because the `EndpointAddress` class is immutable, modification of an endpoint address must be done using the `EndpointAddressBuilder` class.</span></span> <span data-ttu-id="e051b-114">Aşağıdaki kod, iletisinin bir parçası olarak bir başvuru parametresi göndermek için istemcisini başlatır.</span><span class="sxs-lookup"><span data-stu-id="e051b-114">The following code initializes the client to send a reference parameter as part of its message.</span></span>

```csharp
HelloClient client = new HelloClient();
EndpointAddressBuilder builder =
    new EndpointAddressBuilder(client.Endpoint.Address);
AddressHeader header =
    AddressHeader.CreateAddressHeader(IDName, IDNamespace, "John");
builder.Headers.Add(header);
client.Endpoint.Address = builder.ToEndpointAddress();
```

<span data-ttu-id="e051b-115">Kod, özgün `EndpointAddress` bir başlangıç değeri olarak kullanarak bir `EndpointAddressBuilder` oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e051b-115">The code creates an `EndpointAddressBuilder` using the original `EndpointAddress` as an initial value.</span></span> <span data-ttu-id="e051b-116">Daha sonra yeni oluşturulan bir adres üst bilgisi ekler; `CreateAddressHeader` çağrısı, belirli bir ad, ad alanı ve değer içeren bir üst bilgi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e051b-116">It then adds a newly created address header; the call to `CreateAddressHeader` creates a header with a particular name, namespace, and value.</span></span> <span data-ttu-id="e051b-117">Burada değer "John" dır.</span><span class="sxs-lookup"><span data-stu-id="e051b-117">Here the value is "John".</span></span> <span data-ttu-id="e051b-118">Üst bilgi, oluşturucuya eklendikten sonra, `ToEndpointAddress()` yöntemi (kesilebilir) oluşturucuyu, istemci uç noktasının adres alanına geri atanan (değişmez) bir uç nokta adresine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="e051b-118">Once the header is added to the builder, the `ToEndpointAddress()` method converts the (mutable) builder back into an (immutable) endpoint address, which is assigned back to the client endpoint's Address field.</span></span>

<span data-ttu-id="e051b-119">İstemci `Console.WriteLine(client.Hello());`çağırdığında, hizmet bu adres parametresinin değerini istemcinin ortaya çıkan çıktısında görüldüğü gibi alabilir.</span><span class="sxs-lookup"><span data-stu-id="e051b-119">Now when the client calls `Console.WriteLine(client.Hello());`, the service is able to get the value of this address parameter, as seen in the resulting output of the client.</span></span>

`Hello, John`

## <a name="server"></a><span data-ttu-id="e051b-120">Sunucusu</span><span class="sxs-lookup"><span data-stu-id="e051b-120">Server</span></span>

<span data-ttu-id="e051b-121">`Hello()` hizmet işleminin uygulanması, gelen iletideki üstbilgilerin değerlerini incelemek için geçerli `OperationContext` kullanır.</span><span class="sxs-lookup"><span data-stu-id="e051b-121">The implementation of the service operation `Hello()` uses the current `OperationContext` to inspect the values of the headers on the incoming message.</span></span>

```csharp
string id = null;
// look at headers on incoming message
for (int i = 0;
     i < OperationContext.Current.IncomingMessageHeaders.Count;
     ++i)
{
    MessageHeaderInfo h = OperationContext.Current.IncomingMessageHeaders[i];
    // for any reference parameters with the correct name & namespace
    if (h.IsReferenceParameter &&
        h.Name == IDName &&
        h.Namespace == IDNamespace)
    {
        // read the value of that header
        XmlReader xr = OperationContext.Current.IncomingMessageHeaders.GetReaderAtHeader(i);
        id = xr.ReadElementContentAsString();
    }
}
return "Hello, " + id;
```

<span data-ttu-id="e051b-122">Kod, gelen iletideki tüm üst bilgilerin üzerinde yinelenir ve belirli bir ada sahip başvuru parametreleri olan üst bilgileri arar.</span><span class="sxs-lookup"><span data-stu-id="e051b-122">The code iterates over all the headers on the incoming message, looking for headers that are reference parameters with the particular name and.</span></span> <span data-ttu-id="e051b-123">Parametre bulunduğunda, parametrenin değerini okur ve bunu "ID" değişkeninde depolar.</span><span class="sxs-lookup"><span data-stu-id="e051b-123">When the parameter is found, it reads the value of the parameter and stores it in the "id" variable.</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e051b-124">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="e051b-124">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="e051b-125">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="e051b-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="e051b-126">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="e051b-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="e051b-127">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="e051b-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e051b-128">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="e051b-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e051b-129">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e051b-129">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="e051b-130">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="e051b-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e051b-131">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="e051b-131">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\AddressHeaders`
