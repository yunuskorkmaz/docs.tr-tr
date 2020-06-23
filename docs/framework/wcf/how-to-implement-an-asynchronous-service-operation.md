---
title: 'Nasıl yapılır: Zaman Uyumsuz Bir Hizmet İşlemi Uygulama'
description: WFC 'de zaman uyumsuz bir hizmet işleminin yapısı hakkında bilgi edinin. Bir hizmet işlemi, zaman uyumsuz veya zaman uyumlu olarak uygulanabilir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
ms.openlocfilehash: 5f890bd5124e2353cecee37d163b7f2c65b87fde
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244637"
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a><span data-ttu-id="17f64-104">Nasıl yapılır: Zaman Uyumsuz Bir Hizmet İşlemi Uygulama</span><span class="sxs-lookup"><span data-stu-id="17f64-104">How to: Implement an Asynchronous Service Operation</span></span>
<span data-ttu-id="17f64-105">Windows Communication Foundation (WCF) uygulamalarında, bir hizmet işlemi, istemciye dikte etmeden zaman uyumsuz veya eşzamanlı olarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="17f64-105">In Windows Communication Foundation (WCF) applications, a service operation can be implemented asynchronously or synchronously without dictating to the client how to call it.</span></span> <span data-ttu-id="17f64-106">Örneğin, zaman uyumsuz hizmet işlemleri zaman uyumlu olarak çağrılabilir ve zaman uyumlu hizmet işlemleri zaman uyumsuz olarak çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="17f64-106">For example, asynchronous service operations can be called synchronously, and synchronous service operations can be called asynchronously.</span></span> <span data-ttu-id="17f64-107">İstemci uygulamasında bir işlemin zaman uyumsuz olarak nasıl çağrılacağını gösteren bir örnek için bkz. [nasıl yapılır: hizmet Işlemlerini zaman uyumsuz olarak çağırma](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="17f64-107">For an example that shows how to call an operation asynchronously in a client application, see [How to: Call Service Operations Asynchronously](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span> <span data-ttu-id="17f64-108">Zaman uyumlu ve zaman uyumsuz işlemler hakkında daha fazla bilgi için bkz. [hizmet sözleşmeleri tasarlama](designing-service-contracts.md) ve zaman [uyumlu ve zaman uyumsuz işlemler](synchronous-and-asynchronous-operations.md)</span><span class="sxs-lookup"><span data-stu-id="17f64-108">For more information about synchronous and asynchronous operations, see [Designing Service Contracts](designing-service-contracts.md) and [Synchronous and Asynchronous Operations](synchronous-and-asynchronous-operations.md).</span></span> <span data-ttu-id="17f64-109">Bu konu, zaman uyumsuz bir hizmet işleminin temel yapısını açıklar, kod tamamlanmaz.</span><span class="sxs-lookup"><span data-stu-id="17f64-109">This topic describes the basic structure of an asynchronous service operation, the code is not complete.</span></span> <span data-ttu-id="17f64-110">Hem hizmet hem de istemci taraflarından oluşan tüm bir örnek için bkz. [zaman uyumsuz](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="17f64-110">For a complete example of both the service and client sides, see [Asynchronous](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).</span></span>  
  
### <a name="implement-a-service-operation-asynchronously"></a><span data-ttu-id="17f64-111">Zaman uyumsuz olarak bir hizmet işlemi uygulama</span><span class="sxs-lookup"><span data-stu-id="17f64-111">Implement a service operation asynchronously</span></span>  
  
1. <span data-ttu-id="17f64-112">Hizmet sözleşmeniz sırasında, .NET zaman uyumsuz tasarım yönergelerine göre zaman uyumsuz bir yöntem çifti bildirin.</span><span class="sxs-lookup"><span data-stu-id="17f64-112">In your service contract, declare an asynchronous method pair according to the .NET asynchronous design guidelines.</span></span> <span data-ttu-id="17f64-113">`Begin`Yöntemi bir parametre, geri çağırma nesnesi ve bir durum nesnesi alır ve bir ve döndürür ve <xref:System.IAsyncResult?displayProperty=nameWithType> `End` dönüş değerini döndüren eşleşen bir yöntemi döndürür <xref:System.IAsyncResult?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="17f64-113">The `Begin` method takes a parameter, a callback object, and a state object, and returns a <xref:System.IAsyncResult?displayProperty=nameWithType> and a matching `End` method that takes a <xref:System.IAsyncResult?displayProperty=nameWithType> and returns the return value.</span></span> <span data-ttu-id="17f64-114">Zaman uyumsuz çağrılar hakkında daha fazla bilgi için bkz. [zaman uyumsuz programlama tasarım desenleri](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span><span class="sxs-lookup"><span data-stu-id="17f64-114">For more information about asynchronous calls, see [Asynchronous Programming Design Patterns](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span></span>  
  
2. <span data-ttu-id="17f64-115">`Begin`Zaman uyumsuz yöntem çiftinin yöntemini <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> özniteliğiyle işaretleyin ve <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> özelliğini olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="17f64-115">Mark the `Begin` method of the asynchronous method pair with the <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> attribute and set the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="17f64-116">Örneğin, aşağıdaki kod 1 ve 2. adımları gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="17f64-116">For example, the following code performs steps 1 and 2.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3. <span data-ttu-id="17f64-117">`Begin/End`Zaman uyumsuz tasarım yönergelerine göre hizmet sınıfınızda Yöntem çiftini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="17f64-117">Implement the `Begin/End` method pair in your service class according to the asynchronous design guidelines.</span></span> <span data-ttu-id="17f64-118">Örneğin, aşağıdaki kod örneği, bir dizenin hem zaman uyumsuz hizmet işleminin hem de her bölümünde konsola yazıldığı bir uygulamayı gösterir `Begin` `End` ve işlemin dönüş değeri `End` istemciye döndürülür.</span><span class="sxs-lookup"><span data-stu-id="17f64-118">For example, the following code example shows an implementation in which a string is written to the console in both the `Begin` and `End` portions of the asynchronous service operation, and the return value of the `End` operation is returned to the client.</span></span> <span data-ttu-id="17f64-119">Tüm kod örneği için örnek bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="17f64-119">For the complete code example, see the Example section.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="17f64-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="17f64-120">Example</span></span>  
 <span data-ttu-id="17f64-121">Aşağıdaki kod örnekleri şunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="17f64-121">The following code examples show:</span></span>  
  
1. <span data-ttu-id="17f64-122">İle bir hizmet sözleşmesi arabirimi:</span><span class="sxs-lookup"><span data-stu-id="17f64-122">A service contract interface with:</span></span>  
  
    1. <span data-ttu-id="17f64-123">Zaman uyumlu bir `SampleMethod` işlem.</span><span class="sxs-lookup"><span data-stu-id="17f64-123">A synchronous `SampleMethod` operation.</span></span>  
  
    2. <span data-ttu-id="17f64-124">Zaman uyumsuz bir `BeginSampleMethod` işlem.</span><span class="sxs-lookup"><span data-stu-id="17f64-124">An asynchronous `BeginSampleMethod` operation.</span></span>  
  
    3. <span data-ttu-id="17f64-125">Zaman uyumsuz bir `BeginServiceAsyncMethod` / `EndServiceAsyncMethod` işlem çifti.</span><span class="sxs-lookup"><span data-stu-id="17f64-125">An asynchronous `BeginServiceAsyncMethod`/`EndServiceAsyncMethod` operation pair.</span></span>  
  
2. <span data-ttu-id="17f64-126">Bir nesne kullanan hizmet uygulamasıdır <xref:System.IAsyncResult?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="17f64-126">A service implementation using a <xref:System.IAsyncResult?displayProperty=nameWithType> object.</span></span>  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="17f64-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17f64-127">See also</span></span>

- [<span data-ttu-id="17f64-128">Hizmet Sözleşmeleri Tasarlama</span><span class="sxs-lookup"><span data-stu-id="17f64-128">Designing Service Contracts</span></span>](designing-service-contracts.md)
- [<span data-ttu-id="17f64-129">Zaman Uyumlu ve Zaman Uyumsuz İşlemler</span><span class="sxs-lookup"><span data-stu-id="17f64-129">Synchronous and Asynchronous Operations</span></span>](synchronous-and-asynchronous-operations.md)
