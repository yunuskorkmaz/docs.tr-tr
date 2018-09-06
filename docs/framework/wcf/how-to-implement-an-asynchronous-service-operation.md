---
title: 'Nasıl yapılır: Zaman Uyumsuz Bir Hizmet İşlemi Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
ms.openlocfilehash: eeea3933446a401ad8f556dc546f54122a19a8b5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43723892"
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a><span data-ttu-id="af5de-102">Nasıl yapılır: Zaman Uyumsuz Bir Hizmet İşlemi Uygulama</span><span class="sxs-lookup"><span data-stu-id="af5de-102">How to: Implement an Asynchronous Service Operation</span></span>
<span data-ttu-id="af5de-103">Windows Communication Foundation (WCF) uygulamalar, bir hizmet işlemi zaman uyumlu veya zaman uyumsuz olarak nasıl çağıran istemciye dikte olmadan uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="af5de-103">In Windows Communication Foundation (WCF) applications, a service operation can be implemented asynchronously or synchronously without dictating to the client how to call it.</span></span> <span data-ttu-id="af5de-104">Örneğin, zaman uyumsuz hizmet işlemlerini zaman uyumlu olarak arama ve zaman uyumlu hizmet işlemlerini zaman uyumsuz olarak çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="af5de-104">For example, asynchronous service operations can be calling synchronously, and synchronous service operations can be called asynchronously.</span></span> <span data-ttu-id="af5de-105">İşlem bir istemci uygulamasında zaman uyumsuz olarak çağırma gösteren bir örnek için bkz [nasıl yapılır: hizmet işlemlerini zaman uyumsuz çağrı](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="af5de-105">For an example that shows how to call an operation asynchronously in a client application, see [How to: Call Service Operations Asynchronously](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span> <span data-ttu-id="af5de-106">Zaman uyumlu ve zaman uyumsuz işlemler hakkında daha fazla bilgi için bkz: [Hizmet sözleşmeleri tasarlama](../../../docs/framework/wcf/designing-service-contracts.md) ve [zaman uyumlu ve zaman uyumsuz işlemler](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="af5de-106">For more information about synchronous and asynchronous operations, see [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md) and [Synchronous and Asynchronous Operations](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span></span> <span data-ttu-id="af5de-107">Bu konu zaman uyumsuz bir hizmet işlemi temel yapısını tanımlar, kod tam değil.</span><span class="sxs-lookup"><span data-stu-id="af5de-107">This topic describes the basic structure of an asynchronous service operation, the code is not complete.</span></span> <span data-ttu-id="af5de-108">Hem hizmet hem de istemci tarafında tam bir örnek için bkz. [zaman uyumsuz](https://msdn.microsoft.com/library/833db946-f511-4f64-a26f-2759a11217c7).</span><span class="sxs-lookup"><span data-stu-id="af5de-108">For a complete example of both the service and client sides see [Asynchronous](https://msdn.microsoft.com/library/833db946-f511-4f64-a26f-2759a11217c7).</span></span>  
  
### <a name="implement-a-service-operation-asynchronously"></a><span data-ttu-id="af5de-109">Zaman uyumsuz olarak bir hizmet işlemi uygulama</span><span class="sxs-lookup"><span data-stu-id="af5de-109">Implement a service operation asynchronously</span></span>  
  
1.  <span data-ttu-id="af5de-110">Hizmet sözleşmeniz .NET zaman uyumsuz tasarım yönergelerine göre bir zaman uyumsuz yöntem çifti bildirin.</span><span class="sxs-lookup"><span data-stu-id="af5de-110">In your service contract, declare an asynchronous method pair according to the .NET asynchronous design guidelines.</span></span> <span data-ttu-id="af5de-111">`Begin` Yöntemi, bir parametre, bir geri çağırma nesnesi ve durum nesnesi alır ve döndürür bir <xref:System.IAsyncResult?displayProperty=nameWithType> ile eşleşen bir `End` gereken yöntemini bir <xref:System.IAsyncResult?displayProperty=nameWithType> ve dönüş değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="af5de-111">The `Begin` method takes a parameter, a callback object, and a state object, and returns a <xref:System.IAsyncResult?displayProperty=nameWithType> and a matching `End` method that takes a <xref:System.IAsyncResult?displayProperty=nameWithType> and returns the return value.</span></span> <span data-ttu-id="af5de-112">Zaman uyumsuz çağrılar hakkında daha fazla bilgi için bkz. [zaman uyumsuz programlama desenleri](https://go.microsoft.com/fwlink/?LinkId=248221).</span><span class="sxs-lookup"><span data-stu-id="af5de-112">For more information about asynchronous calls, see [Asynchronous Programming Design Patterns](https://go.microsoft.com/fwlink/?LinkId=248221).</span></span>  
  
2.  <span data-ttu-id="af5de-113">İşareti `Begin` yöntemi ile zaman uyumsuz yöntem çiftinin <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> ayarlayın ve öznitelik <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="af5de-113">Mark the `Begin` method of the asynchronous method pair with the <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> attribute and set the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="af5de-114">Örneğin, aşağıdaki kod, 1 ve 2. adımları gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="af5de-114">For example, the following code performs steps 1 and 2.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3.  <span data-ttu-id="af5de-115">Uygulama `Begin/End` hizmet sınıfınızda zaman uyumsuz tasarım yönergelerine göre yöntemi çifti.</span><span class="sxs-lookup"><span data-stu-id="af5de-115">Implement the `Begin/End` method pair in your service class according to the asynchronous design guidelines.</span></span> <span data-ttu-id="af5de-116">Örneğin, aşağıdaki kod örneği, bir dize yazılır hem de konsol uygulaması gösterir `Begin` ve `End` uyumsuz bir hizmet işlemi ve dönüş değeri bölümlerini `End` işlemdir istemciye döndürülen.</span><span class="sxs-lookup"><span data-stu-id="af5de-116">For example, the following code example shows an implementation in which a string is written to the console in both the `Begin` and `End` portions of the asynchronous service operation, and the return value of the `End` operation is returned to the client.</span></span> <span data-ttu-id="af5de-117">İçin tam kod örneği, örnek bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="af5de-117">For the complete code example, see the Example section.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="af5de-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="af5de-118">Example</span></span>  
 <span data-ttu-id="af5de-119">Aşağıdaki kod örnekleri göster:</span><span class="sxs-lookup"><span data-stu-id="af5de-119">The following code examples show:</span></span>  
  
1.  <span data-ttu-id="af5de-120">Hizmet sözleşme arabirimi ile:</span><span class="sxs-lookup"><span data-stu-id="af5de-120">A service contract interface with:</span></span>  
  
    1.  <span data-ttu-id="af5de-121">Eş zamanlı `SampleMethod` işlemi.</span><span class="sxs-lookup"><span data-stu-id="af5de-121">A synchronous `SampleMethod` operation.</span></span>  
  
    2.  <span data-ttu-id="af5de-122">Zaman uyumsuz `BeginSampleMethod` işlemi.</span><span class="sxs-lookup"><span data-stu-id="af5de-122">An asynchronous `BeginSampleMethod` operation.</span></span>  
  
    3.  <span data-ttu-id="af5de-123">Zaman uyumsuz `BeginServiceAsyncMethod` / `EndServiceAsyncMethod` işlemi çifti.</span><span class="sxs-lookup"><span data-stu-id="af5de-123">An asynchronous `BeginServiceAsyncMethod`/`EndServiceAsyncMethod` operation pair.</span></span>  
  
2.  <span data-ttu-id="af5de-124">Bir hizmet uygulamasını kullanarak bir <xref:System.IAsyncResult?displayProperty=nameWithType> nesne.</span><span class="sxs-lookup"><span data-stu-id="af5de-124">A service implementation using a <xref:System.IAsyncResult?displayProperty=nameWithType> object.</span></span>  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="af5de-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="af5de-125">See Also</span></span>  
 [<span data-ttu-id="af5de-126">Hizmet Sözleşmeleri Tasarlama</span><span class="sxs-lookup"><span data-stu-id="af5de-126">Designing Service Contracts</span></span>](../../../docs/framework/wcf/designing-service-contracts.md)  
 [<span data-ttu-id="af5de-127">Zaman Uyumlu ve Zaman Uyumsuz İşlemler</span><span class="sxs-lookup"><span data-stu-id="af5de-127">Synchronous and Asynchronous Operations</span></span>](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)
