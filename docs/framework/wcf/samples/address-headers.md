---
title: Adres Üstbilgileri
ms.date: 03/30/2017
ms.assetid: b0c94d4a-3bde-4b4d-bb6d-9f12bc3a6940
ms.openlocfilehash: 4ccb309178251b32068d6cdbb81874322f991bb9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62002956"
---
# <a name="address-headers"></a><span data-ttu-id="49820-102">Adres Üstbilgileri</span><span class="sxs-lookup"><span data-stu-id="49820-102">Address Headers</span></span>

<span data-ttu-id="49820-103">Adres üstbilgileri örnek istemciler Windows Communication Foundation (WCF) kullanarak bir hizmet için başvuru parametreleri nasıl geçirebilirsiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="49820-103">The Address Headers sample demonstrates how clients can pass reference parameters to a service using Windows Communication Foundation (WCF).</span></span>

> [!NOTE]
> <span data-ttu-id="49820-104">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="49820-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="49820-105">WS-Addressing belirtimi bir şekilde belirli bir Web Hizmeti uç noktası adresi için bir uç nokta başvurusu kavramını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="49820-105">The WS-Addressing specification defines the notion of an endpoint reference as a way to address a particular Web service endpoint.</span></span> <span data-ttu-id="49820-106">WCF'de, uç nokta başvuruları kullanılarak modellendiği durumda `EndpointAddress` sınıfı - `EndpointAddress` adres alanının türü `ServiceEndpoint` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="49820-106">In WCF, endpoint references are modeled using the `EndpointAddress` class - `EndpointAddress` is the type of the Address field of the `ServiceEndpoint` class.</span></span>

<span data-ttu-id="49820-107">Uç nokta başvuru modelini her başvuru ek tanımlayıcı bilgiler ekleyin bazı başvuru parametreleri devam edebileceğinizden parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="49820-107">Part of the endpoint reference model is that each reference can carry some reference parameters that add extra identifying information.</span></span> <span data-ttu-id="49820-108">WCF'de, bu başvuru parametreleri örnekleri olarak modellenir `AddressHeader` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="49820-108">In WCF, these reference parameters are modeled as instances of `AddressHeader` class.</span></span>

<span data-ttu-id="49820-109">Bu örnekte, bir başvuru parametresi için bir istemci ekler `EndpointAddress` istemcisi bitiş noktası.</span><span class="sxs-lookup"><span data-stu-id="49820-109">In this sample, the client adds a reference parameter to the `EndpointAddress` of the client endpoint.</span></span> <span data-ttu-id="49820-110">Hizmet için bu başvuru parametresi arar ve değeri, "Hello" hizmet işlemi mantığı kullanır.</span><span class="sxs-lookup"><span data-stu-id="49820-110">The service looks for this reference parameter and uses its value in the logic of its "Hello" service operation.</span></span>

## <a name="client"></a><span data-ttu-id="49820-111">İstemci</span><span class="sxs-lookup"><span data-stu-id="49820-111">Client</span></span>

<span data-ttu-id="49820-112">İstemcinin bir başvuru parametresi göndermesini eklemeniz gerekir bir `AddressHeader` için `EndpointAddress` , `ServiceEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="49820-112">For the client to send a reference parameter, it must add an `AddressHeader` to the `EndpointAddress` of the `ServiceEndpoint`.</span></span> <span data-ttu-id="49820-113">Çünkü `EndpointAddress` sınıfı sabit, değiştirilmesini bir uç nokta adresi yapılmalıdır kullanarak `EndpointAddressBuilder` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="49820-113">Because the `EndpointAddress` class is immutable, modification of an endpoint address must be done using the `EndpointAddressBuilder` class.</span></span> <span data-ttu-id="49820-114">Aşağıdaki kod, bir başvuru parametresi kendi iletisinin bir parçası göndermek için istemci başlatır.</span><span class="sxs-lookup"><span data-stu-id="49820-114">The following code initializes the client to send a reference parameter as part of its message.</span></span>

```csharp
HelloClient client = new HelloClient();
EndpointAddressBuilder builder =
    new EndpointAddressBuilder(client.Endpoint.Address);
AddressHeader header =
    AddressHeader.CreateAddressHeader(IDName, IDNamespace, "John");
builder.Headers.Add(header);
client.Endpoint.Address = builder.ToEndpointAddress();
```

<span data-ttu-id="49820-115">Kod oluşturur bir `EndpointAddressBuilder` özgün kullanarak `EndpointAddress` olarak başlangıç değeri.</span><span class="sxs-lookup"><span data-stu-id="49820-115">The code creates an `EndpointAddressBuilder` using the original `EndpointAddress` as an initial value.</span></span> <span data-ttu-id="49820-116">Ardından, yeni oluşturulan adres üstbilgisi ekler; çağrı `CreateAddressHeader` üstbilgi belirli ad, ad ve değer oluşturur.</span><span class="sxs-lookup"><span data-stu-id="49820-116">It then adds a newly created address header; the call to `CreateAddressHeader` creates a header with a particular name, namespace, and value.</span></span> <span data-ttu-id="49820-117">Burada "John" değeridir.</span><span class="sxs-lookup"><span data-stu-id="49820-117">Here the value is "John".</span></span> <span data-ttu-id="49820-118">Oluşturucuya, üst bilgi eklendikten sonra `ToEndpointAddress()` yöntemi (değişebilir) oluşturucu geri istemcisi bitiş noktasının adresini alana atanan geri bir (sabit) uç noktası adresi dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="49820-118">Once the header is added to the builder, the `ToEndpointAddress()` method converts the (mutable) builder back into an (immutable) endpoint address, which is assigned back to the client endpoint's Address field.</span></span>

<span data-ttu-id="49820-119">Artık istemciyi çağırdığında `Console.WriteLine(client.Hello());`, istemcinin elde edilen çıktıda görüldüğü şekilde hizmet bu adresi parametresinin değeri alınamadı.</span><span class="sxs-lookup"><span data-stu-id="49820-119">Now when the client calls `Console.WriteLine(client.Hello());`, the service is able to get the value of this address parameter, as seen in the resulting output of the client.</span></span>

`Hello, John`

## <a name="server"></a><span data-ttu-id="49820-120">Sunucu</span><span class="sxs-lookup"><span data-stu-id="49820-120">Server</span></span>

<span data-ttu-id="49820-121">Hizmet işlemi uygulama `Hello()` geçerli kullanan `OperationContext` gelen ileti üst bilgilere değerlerini incelemek için.</span><span class="sxs-lookup"><span data-stu-id="49820-121">The implementation of the service operation `Hello()` uses the current `OperationContext` to inspect the values of the headers on the incoming message.</span></span>

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

<span data-ttu-id="49820-122">Kod, başvuru parametreleri belirli bir ada sahip olan üst aranıyor gelen ileti, tüm üst bilgilere üzerinden yinelenir ve.</span><span class="sxs-lookup"><span data-stu-id="49820-122">The code iterates over all the headers on the incoming message, looking for headers that are reference parameters with the particular name and.</span></span> <span data-ttu-id="49820-123">Parametre bulunduğunda, parametre değerini okur ve "id" değişkeninde depolar.</span><span class="sxs-lookup"><span data-stu-id="49820-123">When the parameter is found, it reads the value of the parameter and stores it in the "id" variable.</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="49820-124">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="49820-124">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="49820-125">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="49820-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="49820-126">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="49820-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="49820-127">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="49820-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="49820-128">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="49820-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="49820-129">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="49820-129">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="49820-130">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="49820-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="49820-131">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="49820-131">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\AddressHeaders`
