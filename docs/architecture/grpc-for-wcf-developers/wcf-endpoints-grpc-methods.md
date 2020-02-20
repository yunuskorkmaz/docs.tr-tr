---
title: WCF son noktaları ve gRPC yöntemleri-WCF geliştiricileri için gRPC
description: ServiceContract ve OperationContract öznitelikleriyle belirtilen WCF uç noktalarının karşılaştırılması ve Protoarabelleğe göre belirtilen gRPC yöntemleri
ms.date: 09/02/2019
ms.openlocfilehash: 1bc6ecbc73bfc0a58393e4c28672b897ed6f2f15
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503426"
---
# <a name="wcf-endpoints-and-grpc-methods"></a><span data-ttu-id="ac835-103">WCF uç noktaları ve gRPC yöntemleri</span><span class="sxs-lookup"><span data-stu-id="ac835-103">WCF endpoints and gRPC methods</span></span>

<span data-ttu-id="ac835-104">Windows Communication Foundation (WCF) ' de, uygulama kodunuzu yazarken aşağıdaki yöntemlerden birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="ac835-104">In Windows Communication Foundation (WCF), when you're writing your application code, you use one of the following methods:</span></span>

- <span data-ttu-id="ac835-105">Uygulama kodunu, OperationContract özniteliğiyle bir sınıfa ve [süsleme](xref:System.ServiceModel.OperationContractAttribute) yöntemlerine yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="ac835-105">You write the application code in a class and decorate methods with the [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attribute.</span></span>
- <span data-ttu-id="ac835-106">Hizmet için bir arabirim bildirir ve arabirime [OperationContract](xref:System.ServiceModel.OperationContractAttribute) öznitelikleri eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="ac835-106">You declare an interface for the service and add [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attributes to the interface.</span></span>

<span data-ttu-id="ac835-107">Örneğin, `greet.proto` Greeter hizmetinin WCF eşdeğeri aşağıdaki gibi yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="ac835-107">For example, the WCF equivalent of the `greet.proto` Greeter service might be written as follows:</span></span>

```csharp
[ServiceContract]
public interface IGreeterService
{
    [OperationContract]
    string SayHello(string name);
}
```

<span data-ttu-id="ac835-108">Bölüm 3 ' te, prototip ileti tanımlarının veri sınıfları oluşturmak için kullanıldığını gösterdi.</span><span class="sxs-lookup"><span data-stu-id="ac835-108">Chapter 3 showed that Protobuf message definitions are used to generate data classes.</span></span> <span data-ttu-id="ac835-109">Hizmeti ve yöntem bildirimleri, hizmetini uygulamak için ' den devraldığı temel sınıfları oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ac835-109">Service and method declarations are used to generate base classes that you inherit from to implement the service.</span></span> <span data-ttu-id="ac835-110">`.proto` dosyasında uygulanacak yöntemleri bildirmeniz yeterlidir ve derleyici, geçersiz kılmanız gereken sanal yöntemlerle bir temel sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ac835-110">You just declare the methods to be implemented in the `.proto` file, and the compiler generates a base class with virtual methods that you must override.</span></span>

## <a name="operationcontract-properties"></a><span data-ttu-id="ac835-111">OperationContract özellikleri</span><span class="sxs-lookup"><span data-stu-id="ac835-111">OperationContract properties</span></span>

<span data-ttu-id="ac835-112">[OperationContract](xref:System.ServiceModel.OperationContractAttribute) özniteliği, nasıl çalıştığını denetlemek veya iyileştirmek için özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ac835-112">The [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attribute has properties to control or refine how it works.</span></span> <span data-ttu-id="ac835-113">gRPC metotları bu tür bir denetim sunmaz.</span><span class="sxs-lookup"><span data-stu-id="ac835-113">gRPC methods don't offer this type of control.</span></span> <span data-ttu-id="ac835-114">Aşağıdaki tabloda bu `OperationContract` özellikleri listelenmekte ve bu işlevlerin gRPC 'de nasıl ele aldığı (veya olmadığı) açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="ac835-114">The following table lists those `OperationContract` properties and describes how the functionality that they specify is (or isn't) dealt with in gRPC:</span></span>

| <span data-ttu-id="ac835-115">`OperationContract` özelliği</span><span class="sxs-lookup"><span data-stu-id="ac835-115">`OperationContract` property</span></span> | <span data-ttu-id="ac835-116">gRPC</span><span class="sxs-lookup"><span data-stu-id="ac835-116">gRPC</span></span>                                             |
| ---------------------------- | ------------------------------------------------ |
| <xref:System.ServiceModel.OperationContractAttribute.Action>             | <span data-ttu-id="ac835-117">Bir URI, işlemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ac835-117">A URI identifies the operation.</span></span> <span data-ttu-id="ac835-118">gRPC, `.proto` dosyasından `package`, `service`ve `rpc` adını kullanır.</span><span class="sxs-lookup"><span data-stu-id="ac835-118">gRPC uses the name of `package`, `service`, and `rpc` from the `.proto` file.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern>       | <span data-ttu-id="ac835-119">Tüm gRPC hizmet yöntemleri `Task` nesneleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="ac835-119">All gRPC service methods return `Task` objects.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsInitiating>       | <span data-ttu-id="ac835-120">Bu tablodan sonraki paragrafa bakın.</span><span class="sxs-lookup"><span data-stu-id="ac835-120">See the paragraph after this table.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsOneWay>           | <span data-ttu-id="ac835-121">Tek yönlü gRPC yöntemleri `Empty` sonuçları döndürür veya istemci akışını kullanır.</span><span class="sxs-lookup"><span data-stu-id="ac835-121">One-way gRPC methods return `Empty` results or use client streaming.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsTerminating>      | <span data-ttu-id="ac835-122">Bu tablodan sonraki paragrafa bakın.</span><span class="sxs-lookup"><span data-stu-id="ac835-122">See the paragraph after this table.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.Name>               | <span data-ttu-id="ac835-123">Bu özellik SOAP ile ilgilidir ve gRPC 'de bir anlamı yoktur.</span><span class="sxs-lookup"><span data-stu-id="ac835-123">This property is SOAP related and has no meaning in gRPC.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel>    | <span data-ttu-id="ac835-124">İleti şifrelemesi yok.</span><span class="sxs-lookup"><span data-stu-id="ac835-124">There's no message encryption.</span></span> <span data-ttu-id="ac835-125">Ağ şifreleme, aktarım katmanında (HTTP/2 üzerinden TLS) işlenir.</span><span class="sxs-lookup"><span data-stu-id="ac835-125">Network encryption is handled at the transport layer (TLS over HTTP/2).</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.ReplyAction>        | <span data-ttu-id="ac835-126">Bu özellik SOAP ile ilgilidir ve gRPC 'de bir anlamı yoktur.</span><span class="sxs-lookup"><span data-stu-id="ac835-126">This property is SOAP related and has no meaning in gRPC.</span></span> |

<span data-ttu-id="ac835-127">`IsInitiating` özelliği, [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) içindeki bir yöntemin bir oturumun parçası olarak çağrılan ilk yöntem olabileceğini belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="ac835-127">The `IsInitiating` property lets you indicate that a method within [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) can't be the first method called as part of a session.</span></span> <span data-ttu-id="ac835-128">`IsTerminating` özelliği, bir işlem çağrıldıktan sonra sunucunun oturumu kapatmasına neden olur (veya özellik bir geri çağırma istemcisinde kullanılıyorsa istemci).</span><span class="sxs-lookup"><span data-stu-id="ac835-128">The `IsTerminating` property causes the server to close the session after an operation is called (or the client, if the property is used on a callback client).</span></span> <span data-ttu-id="ac835-129">GRPC 'de akışlar tek yöntemlerle oluşturulur ve açıkça kapatılır.</span><span class="sxs-lookup"><span data-stu-id="ac835-129">In gRPC, streams are created by single methods and closed explicitly.</span></span> <span data-ttu-id="ac835-130">Bkz. [GRPC akışı](rpc-types.md#grpc-streaming).</span><span class="sxs-lookup"><span data-stu-id="ac835-130">See [gRPC streaming](rpc-types.md#grpc-streaming).</span></span>

<span data-ttu-id="ac835-131">GRPC güvenliği ve şifreleme hakkında daha fazla bilgi için bkz. [Bölüm 6](security.md).</span><span class="sxs-lookup"><span data-stu-id="ac835-131">For more information on gRPC security and encryption, see [chapter 6](security.md).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ac835-132">[Önceki](wcf-services-to-grpc-comparison.md)
>[İleri](wcf-bindings.md)</span><span class="sxs-lookup"><span data-stu-id="ac835-132">[Previous](wcf-services-to-grpc-comparison.md)
[Next](wcf-bindings.md)</span></span>
