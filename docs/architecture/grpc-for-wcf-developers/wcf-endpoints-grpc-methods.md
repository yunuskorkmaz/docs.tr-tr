---
title: WCF son noktaları ve gRPC yöntemleri-WCF geliştiricileri için gRPC
description: ServiceContract ve OperationContract öznitelikleriyle belirtilen WCF uç noktalarının karşılaştırılması ve Protoarabelleğe göre belirtilen gRPC yöntemleri
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 08f2d0874417c0ca319b0c193e6108536376d693
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184066"
---
# <a name="wcf-endpoints-and-grpc-methods"></a><span data-ttu-id="1c046-103">WCF uç noktaları ve gRPC yöntemleri</span><span class="sxs-lookup"><span data-stu-id="1c046-103">WCF endpoints and gRPC methods</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="1c046-104">WCF 'de, uygulama kodunuzu yazarken aşağıdaki yöntemlerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="1c046-104">In WCF, when you're writing your application code, you use one of the following methods:</span></span>

- <span data-ttu-id="1c046-105">Uygulama kodunu, OperationContract özniteliğiyle bir sınıfa ve [süsleme](xref:System.ServiceModel.OperationContractAttribute) yöntemlerine yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="1c046-105">You write the application code in a class and decorate methods with the [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attribute.</span></span>
- <span data-ttu-id="1c046-106">Hizmet için bir arabirim bildirir ve arabirime [OperationContract](xref:System.ServiceModel.OperationContractAttribute) öznitelikleri eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="1c046-106">You declare an interface for the service and add [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attributes to the interface.</span></span>

<span data-ttu-id="1c046-107">Örneğin, `greet.proto` Greeter hizmetinin WCF eşdeğeri aşağıdaki gibi yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="1c046-107">For example, the WCF equivalent of the `greet.proto` Greeter service might be written as follows:</span></span>

```csharp
[ServiceContract]
public interface IGreeterService
{
    [OperationContract]
    string SayHello(string name);
}
```

<span data-ttu-id="1c046-108">Bölüm 3 ' te, prototip ileti tanımlarının veri sınıfları oluşturmak için kullanıldığını gösterdi.</span><span class="sxs-lookup"><span data-stu-id="1c046-108">Chapter 3 showed that Protobuf message definitions are used to generate data classes.</span></span> <span data-ttu-id="1c046-109">Hizmeti ve yöntem bildirimleri, hizmetini uygulamak için ' den devraldığı temel sınıfları oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1c046-109">Service and method declarations are used to generate base classes that you inherit from to implement the service.</span></span> <span data-ttu-id="1c046-110">Yalnızca `.proto` dosyada uygulanacak yöntemleri bildirmeniz ve derleyici, sanal yöntemlerle geçersiz kılmanız gereken bir temel sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1c046-110">You just declare the methods to be implemented in the `.proto` file, and the compiler generates a base class with virtual methods you must override.</span></span>

## <a name="operationcontract-properties"></a><span data-ttu-id="1c046-111">OperationContract özellikleri</span><span class="sxs-lookup"><span data-stu-id="1c046-111">OperationContract properties</span></span>

<span data-ttu-id="1c046-112">[OperationContract](xref:System.ServiceModel.OperationContractAttribute) özniteliği, nasıl çalıştığını denetlemek veya iyileştirmek için özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1c046-112">The [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attribute has properties to control or refine how it works.</span></span> <span data-ttu-id="1c046-113">gRPC metotları bu tür bir denetim sunmaz.</span><span class="sxs-lookup"><span data-stu-id="1c046-113">gRPC methods don’t offer this type of control.</span></span> <span data-ttu-id="1c046-114">Aşağıdaki tabloda, bu özellikler ve `OperationContract` bu özelliklerin, GRPC 'de ile nasıl ele aldığı (veya değil) olduğu işlevleri ayarlanır:</span><span class="sxs-lookup"><span data-stu-id="1c046-114">The following table sets out those `OperationContract` properties and how the functionality they specify is (or isn’t) dealt with in gRPC:</span></span>

| <span data-ttu-id="1c046-115">`OperationContract`özelliði</span><span class="sxs-lookup"><span data-stu-id="1c046-115">`OperationContract` property</span></span> | <span data-ttu-id="1c046-116">gRPC</span><span class="sxs-lookup"><span data-stu-id="1c046-116">gRPC</span></span>                                             |
| ---------------------------- | ------------------------------------------------ |
| <xref:System.ServiceModel.OperationContractAttribute.Action>             | <span data-ttu-id="1c046-117">İşlemi tanımlayan URI.</span><span class="sxs-lookup"><span data-stu-id="1c046-117">URI identifying the operation.</span></span> <span data-ttu-id="1c046-118">`package`GRPC, `service` dosyanın`.proto` adını ve `rpc` dosyasından kullanır.</span><span class="sxs-lookup"><span data-stu-id="1c046-118">gRPC uses the name of the `package`, `service` and `rpc` from the `.proto` file.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern>       | <span data-ttu-id="1c046-119">Tüm GRPC hizmet yöntemleri nesneleri `Task` döndürür.</span><span class="sxs-lookup"><span data-stu-id="1c046-119">All gRPC service methods return `Task` objects.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsInitiating>       | <span data-ttu-id="1c046-120">Aşağıdaki nota bakın.</span><span class="sxs-lookup"><span data-stu-id="1c046-120">See note below.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsOneWay>           | <span data-ttu-id="1c046-121">Tek yönlü GRPC yöntemleri sonuçları döndürür `Empty` veya istemci akışını kullanır.</span><span class="sxs-lookup"><span data-stu-id="1c046-121">One-way gRPC methods return `Empty` results or use client streaming.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsTerminating>      | <span data-ttu-id="1c046-122">Aşağıdaki nota bakın.</span><span class="sxs-lookup"><span data-stu-id="1c046-122">See note below.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.Name>               | <span data-ttu-id="1c046-123">GRPC 'de anlamı olmayan SOAP ile ilgili.</span><span class="sxs-lookup"><span data-stu-id="1c046-123">SOAP-related, no meaning in gRPC.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel>    | <span data-ttu-id="1c046-124">İleti şifrelemesi yok; ağ şifrelemesi aktarım katmanında işlendi (HTTP/2 üzerinden TLS).</span><span class="sxs-lookup"><span data-stu-id="1c046-124">No message encryption; network encryption handled at the transport layer (TLS over HTTP/2).</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.ReplyAction>        | <span data-ttu-id="1c046-125">GRPC 'de anlamı olmayan SOAP ile ilgili.</span><span class="sxs-lookup"><span data-stu-id="1c046-125">SOAP-related, no meaning in gRPC.</span></span> |

<span data-ttu-id="1c046-126">Özelliği `IsInitiating` , bir [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) içindeki bir yöntemin bir oturumun parçası olarak çağrılan ilk yöntem olabileceğini belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="1c046-126">The `IsInitiating` property lets you indicate that a method within a [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) can't be the first method called as part of a session.</span></span> <span data-ttu-id="1c046-127">`IsTerminating` Özelliği, bir işlem çağrıldıktan sonra sunucunun oturumu kapatmasına neden olur (veya bir geri çağırma istemcisinde kullanılıyorsa istemci).</span><span class="sxs-lookup"><span data-stu-id="1c046-127">The `IsTerminating` property causes the server to close the session after an operation is called (or the client, if used on a callback client).</span></span> <span data-ttu-id="1c046-128">GRPC 'de akışlar tek yöntemlerle oluşturulur ve açıkça kapatılır.</span><span class="sxs-lookup"><span data-stu-id="1c046-128">In gRPC, streams are created by single methods and closed explicitly.</span></span> <span data-ttu-id="1c046-129">Bkz. [GRPC akışı](rpc-types.md#grpc-streaming).</span><span class="sxs-lookup"><span data-stu-id="1c046-129">See [gRPC streaming](rpc-types.md#grpc-streaming).</span></span>

<span data-ttu-id="1c046-130">GRPC güvenliği ve şifreleme hakkında daha fazla bilgi için bkz. [Bölüm 6](security.md).</span><span class="sxs-lookup"><span data-stu-id="1c046-130">For more information on gRPC security and encryption, see [chapter 6](security.md).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1c046-131">[Önceki](wcf-services-to-grpc-comparison.md)
>[İleri](wcf-bindings.md)</span><span class="sxs-lookup"><span data-stu-id="1c046-131">[Previous](wcf-services-to-grpc-comparison.md)
[Next](wcf-bindings.md)</span></span>
