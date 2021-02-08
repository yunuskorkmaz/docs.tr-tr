---
description: 'Daha fazla bilgi edinin: adres üstbilgileri'
title: Adres Üstbilgileri
ms.date: 03/30/2017
ms.assetid: b0c94d4a-3bde-4b4d-bb6d-9f12bc3a6940
ms.openlocfilehash: a0b421776e1b6b792fa237e0cd65f9686198194e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779198"
---
# <a name="address-headers"></a><span data-ttu-id="5d4b4-103">Adres Üstbilgileri</span><span class="sxs-lookup"><span data-stu-id="5d4b4-103">Address Headers</span></span>

<span data-ttu-id="5d4b4-104">Adres üstbilgileri örneği, istemcilerin Windows Communication Foundation (WCF) kullanarak başvuru parametrelerini bir hizmete nasıl geçirebileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="5d4b4-104">The Address Headers sample demonstrates how clients can pass reference parameters to a service using Windows Communication Foundation (WCF).</span></span>

> [!NOTE]
> <span data-ttu-id="5d4b4-105">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="5d4b4-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="5d4b4-106">WS-Addressing belirtimi, belirli bir Web hizmeti uç noktasını ele almanın bir yolu olarak bir uç nokta başvurusunun kavramını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5d4b4-106">The WS-Addressing specification defines the notion of an endpoint reference as a way to address a particular Web service endpoint.</span></span> <span data-ttu-id="5d4b4-107">WCF 'de, uç nokta başvuruları sınıfı kullanılarak modellenir, `EndpointAddress` `EndpointAddress` sınıfının adres alanının türüdür `ServiceEndpoint` .</span><span class="sxs-lookup"><span data-stu-id="5d4b4-107">In WCF, endpoint references are modeled using the `EndpointAddress` class - `EndpointAddress` is the type of the Address field of the `ServiceEndpoint` class.</span></span>

<span data-ttu-id="5d4b4-108">Uç nokta başvuru modelinin bir bölümü, her başvurunun ek tanımlayıcı bilgi ekleyen bazı başvuru parametrelerini taşıyacağından oluşur.</span><span class="sxs-lookup"><span data-stu-id="5d4b4-108">Part of the endpoint reference model is that each reference can carry some reference parameters that add extra identifying information.</span></span> <span data-ttu-id="5d4b4-109">WCF 'de, bu başvuru parametreleri sınıfının örnekleri olarak modellenir `AddressHeader` .</span><span class="sxs-lookup"><span data-stu-id="5d4b4-109">In WCF, these reference parameters are modeled as instances of `AddressHeader` class.</span></span>

<span data-ttu-id="5d4b4-110">Bu örnekte istemci, istemci uç noktasının öğesine bir başvuru parametresi ekler `EndpointAddress` .</span><span class="sxs-lookup"><span data-stu-id="5d4b4-110">In this sample, the client adds a reference parameter to the `EndpointAddress` of the client endpoint.</span></span> <span data-ttu-id="5d4b4-111">Hizmet bu başvuru parametresini arar ve "Hello" hizmet işleminin mantığındaki değerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="5d4b4-111">The service looks for this reference parameter and uses its value in the logic of its "Hello" service operation.</span></span>

## <a name="client"></a><span data-ttu-id="5d4b4-112">İstemci</span><span class="sxs-lookup"><span data-stu-id="5d4b4-112">Client</span></span>

<span data-ttu-id="5d4b4-113">İstemcisinin bir başvuru parametresi gönderebilmesi için, `AddressHeader` öğesinin öğesine öğesine eklemesi gerekir `EndpointAddress` `ServiceEndpoint` .</span><span class="sxs-lookup"><span data-stu-id="5d4b4-113">For the client to send a reference parameter, it must add an `AddressHeader` to the `EndpointAddress` of the `ServiceEndpoint`.</span></span> <span data-ttu-id="5d4b4-114">`EndpointAddress`Sınıf sabit olduğundan, bir uç nokta adresinin değiştirilmesi sınıfı kullanılarak yapılmalıdır `EndpointAddressBuilder` .</span><span class="sxs-lookup"><span data-stu-id="5d4b4-114">Because the `EndpointAddress` class is immutable, modification of an endpoint address must be done using the `EndpointAddressBuilder` class.</span></span> <span data-ttu-id="5d4b4-115">Aşağıdaki kod, iletisinin bir parçası olarak bir başvuru parametresi göndermek için istemcisini başlatır.</span><span class="sxs-lookup"><span data-stu-id="5d4b4-115">The following code initializes the client to send a reference parameter as part of its message.</span></span>

```csharp
HelloClient client = new HelloClient();
EndpointAddressBuilder builder =
    new EndpointAddressBuilder(client.Endpoint.Address);
AddressHeader header =
    AddressHeader.CreateAddressHeader(IDName, IDNamespace, "John");
builder.Headers.Add(header);
client.Endpoint.Address = builder.ToEndpointAddress();
```

<span data-ttu-id="5d4b4-116">Kod, başlangıçtaki `EndpointAddressBuilder` değeri olarak bir using `EndpointAddress` değeri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5d4b4-116">The code creates an `EndpointAddressBuilder` using the original `EndpointAddress` as an initial value.</span></span> <span data-ttu-id="5d4b4-117">Daha sonra yeni oluşturulan bir adres üst bilgisi ekler; çağrısı, `CreateAddressHeader` belirli bir ad, ad alanı ve değer içeren bir üst bilgi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5d4b4-117">It then adds a newly created address header; the call to `CreateAddressHeader` creates a header with a particular name, namespace, and value.</span></span> <span data-ttu-id="5d4b4-118">Burada değer "John" dır.</span><span class="sxs-lookup"><span data-stu-id="5d4b4-118">Here the value is "John".</span></span> <span data-ttu-id="5d4b4-119">Üstbilgi, oluşturucuya eklendikten sonra, `ToEndpointAddress()` Yöntemi (kesilebilir) oluşturucuyu, istemci uç noktasının adres alanına geri atanan bir (değişmez) uç nokta adresine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="5d4b4-119">Once the header is added to the builder, the `ToEndpointAddress()` method converts the (mutable) builder back into an (immutable) endpoint address, which is assigned back to the client endpoint's Address field.</span></span>

<span data-ttu-id="5d4b4-120">Artık istemci çağırdığında `Console.WriteLine(client.Hello());` , hizmet bu adres parametresinin değerini istemcinin ortaya çıkan çıktısında görüldüğü gibi alabilir.</span><span class="sxs-lookup"><span data-stu-id="5d4b4-120">Now when the client calls `Console.WriteLine(client.Hello());`, the service is able to get the value of this address parameter, as seen in the resulting output of the client.</span></span>

`Hello, John`

## <a name="server"></a><span data-ttu-id="5d4b4-121">Sunucu</span><span class="sxs-lookup"><span data-stu-id="5d4b4-121">Server</span></span>

<span data-ttu-id="5d4b4-122">Hizmet işleminin uygulanması, `Hello()` `OperationContext` gelen iletideki üst bilgilerin değerlerini incelemek için geçerli öğeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="5d4b4-122">The implementation of the service operation `Hello()` uses the current `OperationContext` to inspect the values of the headers on the incoming message.</span></span>

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

<span data-ttu-id="5d4b4-123">Kod, gelen iletideki tüm üst bilgilerin üzerinde yinelenir ve belirli bir ada sahip başvuru parametreleri olan üst bilgileri arar.</span><span class="sxs-lookup"><span data-stu-id="5d4b4-123">The code iterates over all the headers on the incoming message, looking for headers that are reference parameters with the particular name and.</span></span> <span data-ttu-id="5d4b4-124">Parametre bulunduğunda, parametrenin değerini okur ve bunu "ID" değişkeninde depolar.</span><span class="sxs-lookup"><span data-stu-id="5d4b4-124">When the parameter is found, it reads the value of the parameter and stores it in the "id" variable.</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5d4b4-125">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="5d4b4-125">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="5d4b4-126">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="5d4b4-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="5d4b4-127">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="5d4b4-127">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="5d4b4-128">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="5d4b4-128">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5d4b4-129">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="5d4b4-129">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5d4b4-130">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5d4b4-130">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="5d4b4-131">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5d4b4-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5d4b4-132">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="5d4b4-132">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\AddressHeaders`
