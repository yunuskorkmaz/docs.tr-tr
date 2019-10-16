---
title: 'Nasıl yapılır: Zaman Uyumsuz Bir Hizmet İşlemi Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
ms.openlocfilehash: b706ec49db123f33b3fc1ab0f420ed9a47e32f67
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320949"
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a><span data-ttu-id="ac693-102">Nasıl yapılır: Zaman Uyumsuz Bir Hizmet İşlemi Uygulama</span><span class="sxs-lookup"><span data-stu-id="ac693-102">How to: Implement an Asynchronous Service Operation</span></span>
<span data-ttu-id="ac693-103">Windows Communication Foundation (WCF) uygulamalarında, bir hizmet işlemi, istemciye dikte etmeden zaman uyumsuz veya eşzamanlı olarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="ac693-103">In Windows Communication Foundation (WCF) applications, a service operation can be implemented asynchronously or synchronously without dictating to the client how to call it.</span></span> <span data-ttu-id="ac693-104">Örneğin, zaman uyumsuz hizmet işlemleri zaman uyumlu olarak çağrılabilir ve zaman uyumlu hizmet işlemleri zaman uyumsuz olarak çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="ac693-104">For example, asynchronous service operations can be called synchronously, and synchronous service operations can be called asynchronously.</span></span> <span data-ttu-id="ac693-105">İstemci uygulamasında bir işlemin zaman uyumsuz olarak nasıl çağrılacağını gösteren bir örnek için bkz. [nasıl yapılır: hizmet Işlemlerini zaman uyumsuz olarak çağırma](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="ac693-105">For an example that shows how to call an operation asynchronously in a client application, see [How to: Call Service Operations Asynchronously](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span> <span data-ttu-id="ac693-106">Zaman uyumlu ve zaman uyumsuz işlemler hakkında daha fazla bilgi için bkz. [hizmet sözleşmeleri tasarlama](designing-service-contracts.md) ve zaman [uyumlu ve zaman uyumsuz işlemler](synchronous-and-asynchronous-operations.md)</span><span class="sxs-lookup"><span data-stu-id="ac693-106">For more information about synchronous and asynchronous operations, see [Designing Service Contracts](designing-service-contracts.md) and [Synchronous and Asynchronous Operations](synchronous-and-asynchronous-operations.md).</span></span> <span data-ttu-id="ac693-107">Bu konu, zaman uyumsuz bir hizmet işleminin temel yapısını açıklar, kod tamamlanmaz.</span><span class="sxs-lookup"><span data-stu-id="ac693-107">This topic describes the basic structure of an asynchronous service operation, the code is not complete.</span></span> <span data-ttu-id="ac693-108">Hem hizmet hem de istemci taraflarından oluşan tüm bir örnek için bkz. [zaman uyumsuz](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ac693-108">For a complete example of both the service and client sides, see [Asynchronous](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).</span></span>  
  
### <a name="implement-a-service-operation-asynchronously"></a><span data-ttu-id="ac693-109">Zaman uyumsuz olarak bir hizmet işlemi uygulama</span><span class="sxs-lookup"><span data-stu-id="ac693-109">Implement a service operation asynchronously</span></span>  
  
1. <span data-ttu-id="ac693-110">Hizmet sözleşmeniz sırasında, .NET zaman uyumsuz tasarım yönergelerine göre zaman uyumsuz bir yöntem çifti bildirin.</span><span class="sxs-lookup"><span data-stu-id="ac693-110">In your service contract, declare an asynchronous method pair according to the .NET asynchronous design guidelines.</span></span> <span data-ttu-id="ac693-111">@No__t-0 yöntemi bir parametre, geri çağırma nesnesi ve bir durum nesnesi alır ve bir <xref:System.IAsyncResult?displayProperty=nameWithType> ve eşleşen `End` yöntemi döndürür ve <xref:System.IAsyncResult?displayProperty=nameWithType> alır ve döndürülen değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="ac693-111">The `Begin` method takes a parameter, a callback object, and a state object, and returns a <xref:System.IAsyncResult?displayProperty=nameWithType> and a matching `End` method that takes a <xref:System.IAsyncResult?displayProperty=nameWithType> and returns the return value.</span></span> <span data-ttu-id="ac693-112">Zaman uyumsuz çağrılar hakkında daha fazla bilgi için bkz. [zaman uyumsuz programlama tasarım desenleri](https://go.microsoft.com/fwlink/?LinkId=248221).</span><span class="sxs-lookup"><span data-stu-id="ac693-112">For more information about asynchronous calls, see [Asynchronous Programming Design Patterns](https://go.microsoft.com/fwlink/?LinkId=248221).</span></span>  
  
2. <span data-ttu-id="ac693-113">Zaman uyumsuz yöntem çiftinin `Begin` yöntemini <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> özniteliğiyle işaretleyin ve <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> özelliğini `true` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ac693-113">Mark the `Begin` method of the asynchronous method pair with the <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> attribute and set the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="ac693-114">Örneğin, aşağıdaki kod 1 ve 2. adımları gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="ac693-114">For example, the following code performs steps 1 and 2.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3. <span data-ttu-id="ac693-115">Zaman uyumsuz tasarım yönergelerine göre hizmet sınıfınızda `Begin/End` Yöntem çiftini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="ac693-115">Implement the `Begin/End` method pair in your service class according to the asynchronous design guidelines.</span></span> <span data-ttu-id="ac693-116">Örneğin, aşağıdaki kod örneğinde bir dizenin, zaman uyumsuz hizmet işleminin hem `Begin` hem de `End` bölümlerinde konsola yazıldığı bir uygulama gösterilmektedir ve `End` işleminin dönüş değeri istemciye döndürülür.</span><span class="sxs-lookup"><span data-stu-id="ac693-116">For example, the following code example shows an implementation in which a string is written to the console in both the `Begin` and `End` portions of the asynchronous service operation, and the return value of the `End` operation is returned to the client.</span></span> <span data-ttu-id="ac693-117">Tüm kod örneği için örnek bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="ac693-117">For the complete code example, see the Example section.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="ac693-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac693-118">Example</span></span>  
 <span data-ttu-id="ac693-119">Aşağıdaki kod örnekleri şunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="ac693-119">The following code examples show:</span></span>  
  
1. <span data-ttu-id="ac693-120">İle bir hizmet sözleşmesi arabirimi:</span><span class="sxs-lookup"><span data-stu-id="ac693-120">A service contract interface with:</span></span>  
  
    1. <span data-ttu-id="ac693-121">Zaman uyumlu `SampleMethod` işlemi.</span><span class="sxs-lookup"><span data-stu-id="ac693-121">A synchronous `SampleMethod` operation.</span></span>  
  
    2. <span data-ttu-id="ac693-122">Zaman uyumsuz bir `BeginSampleMethod` işlemi.</span><span class="sxs-lookup"><span data-stu-id="ac693-122">An asynchronous `BeginSampleMethod` operation.</span></span>  
  
    3. <span data-ttu-id="ac693-123">Zaman uyumsuz bir `BeginServiceAsyncMethod` @ no__t-1 @ no__t-2 işlem çifti.</span><span class="sxs-lookup"><span data-stu-id="ac693-123">An asynchronous `BeginServiceAsyncMethod`/`EndServiceAsyncMethod` operation pair.</span></span>  
  
2. <span data-ttu-id="ac693-124">@No__t-0 nesnesi kullanan bir hizmet uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="ac693-124">A service implementation using a <xref:System.IAsyncResult?displayProperty=nameWithType> object.</span></span>  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ac693-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac693-125">See also</span></span>

- [<span data-ttu-id="ac693-126">Hizmet Sözleşmeleri Tasarlama</span><span class="sxs-lookup"><span data-stu-id="ac693-126">Designing Service Contracts</span></span>](designing-service-contracts.md)
- [<span data-ttu-id="ac693-127">Zaman Uyumlu ve Zaman Uyumsuz İşlemler</span><span class="sxs-lookup"><span data-stu-id="ac693-127">Synchronous and Asynchronous Operations</span></span>](synchronous-and-asynchronous-operations.md)
