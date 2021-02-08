---
description: 'Daha fazla bilgi edinin: nasıl yapılır: Kanal fabrikası kullanarak Işlemleri zaman uyumsuz olarak çağırma'
title: 'Nasıl yapılır: Kanal Fabrikası Kullanarak İşlemlere Zaman Uyumsuz Olarak Çağrı Yapma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cc17dd47-b9ad-451c-a362-e36e0aac7ba0
ms.openlocfilehash: 081211d0202550e93e3aabb5c8b5b5b5adbcdcde
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780199"
---
# <a name="how-to-call-operations-asynchronously-using-a-channel-factory"></a><span data-ttu-id="ec57c-103">Nasıl yapılır: Kanal Fabrikası Kullanarak İşlemlere Zaman Uyumsuz Olarak Çağrı Yapma</span><span class="sxs-lookup"><span data-stu-id="ec57c-103">How to: Call Operations Asynchronously Using a Channel Factory</span></span>

<span data-ttu-id="ec57c-104">Bu konu, bir istemcinin bir hizmet işlemine tabanlı bir istemci uygulaması kullanılırken zaman uyumsuz olarak nasıl erişebileceğini ele almaktadır <xref:System.ServiceModel.ChannelFactory%601> .</span><span class="sxs-lookup"><span data-stu-id="ec57c-104">This topic covers how a client can access a service operation asynchronously when using a <xref:System.ServiceModel.ChannelFactory%601>-based client application.</span></span> <span data-ttu-id="ec57c-105">(Bir <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> hizmeti çağırmak için bir nesnesi kullanırken, olay odaklı zaman uyumsuz çağırma modelini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec57c-105">(When using a <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> object to invoke a service you can use the event-driven asynchronous calling model.</span></span> <span data-ttu-id="ec57c-106">Daha fazla bilgi için bkz. [nasıl yapılır: hizmet Işlemlerini zaman uyumsuz olarak çağırma](how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="ec57c-106">For more information, see [How to: Call Service Operations Asynchronously](how-to-call-wcf-service-operations-asynchronously.md).</span></span> <span data-ttu-id="ec57c-107">Olay tabanlı zaman uyumsuz çağrı modeli hakkında daha fazla bilgi için bkz. [olay tabanlı zaman uyumsuz model (EAP)](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).)</span><span class="sxs-lookup"><span data-stu-id="ec57c-107">For more information about the event-based asynchronous calling model, see [Event-based Asynchronous Pattern (EAP)](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).)</span></span>  
  
 <span data-ttu-id="ec57c-108">Bu konudaki hizmet, `ICalculator` arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="ec57c-108">The service in this topic implements the `ICalculator` interface.</span></span> <span data-ttu-id="ec57c-109">İstemci bu arabirimdeki işlemleri zaman uyumsuz olarak çağırabilir. Bu, gibi işlemlerin `Add` iki yönteme bölündüğü `BeginAdd` ve `EndAdd` daha önce çağrıyı başlatan ve bu işlem tamamlandığında sonucu alan, ikincinin oluşturulduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ec57c-109">The client can call the operations on this interface asynchronously, which means that operations like `Add` are split into two methods, `BeginAdd` and `EndAdd`, the former of which initiates the call and the latter of which retrieves the result when the operation completes.</span></span> <span data-ttu-id="ec57c-110">Bir hizmetin bir hizmette zaman uyumsuz olarak nasıl uygulanacağını gösteren bir örnek için bkz. [nasıl yapılır: Işlem zaman uyumsuz hizmet Işlemi uygulama](../how-to-implement-an-asynchronous-service-operation.md).</span><span class="sxs-lookup"><span data-stu-id="ec57c-110">For an example showing how to implement an operation asynchronously in a service, see [How to: Implement an Asynchronous Service Operation](../how-to-implement-an-asynchronous-service-operation.md).</span></span> <span data-ttu-id="ec57c-111">Zaman uyumlu ve zaman uyumsuz işlemler hakkında ayrıntılar için bkz. [zaman uyumlu ve zaman uyumsuz işlemler](../synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="ec57c-111">For details about synchronous and asynchronous operations, see [Synchronous and Asynchronous Operations](../synchronous-and-asynchronous-operations.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="ec57c-112">Yordam</span><span class="sxs-lookup"><span data-stu-id="ec57c-112">Procedure</span></span>  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="ec57c-113">WCF hizmeti işlemlerini zaman uyumsuz olarak çağırma</span><span class="sxs-lookup"><span data-stu-id="ec57c-113">To call WCF service operations asynchronously</span></span>  
  
1. <span data-ttu-id="ec57c-114">Aşağıdaki komutta gösterildiği gibi seçeneğiyle [ServiceModel meta veri yardımcı programı Aracı (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) aracını çalıştırın `/async` .</span><span class="sxs-lookup"><span data-stu-id="ec57c-114">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tool with the `/async` option as shown in the following command.</span></span>  
  
    ```console
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a  
    ```  
  
     <span data-ttu-id="ec57c-115">Bu işlem için hizmet sözleşmesinin zaman uyumsuz bir istemci sürümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ec57c-115">This generates an asynchronous client version of the service contract for the operation.</span></span>  
  
2. <span data-ttu-id="ec57c-116">Aşağıdaki örnek kodda gösterildiği gibi zaman uyumsuz işlem tamamlandığında çağrılacak bir geri arama işlevi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ec57c-116">Create a callback function to be called when the asynchronous operation is complete, as shown in the following sample code.</span></span>  
  
     [!code-csharp[C_How_To_CF_Async#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#2)]
     [!code-vb[C_How_To_CF_Async#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#2)]  
  
3. <span data-ttu-id="ec57c-117">Bir hizmet işlemine zaman uyumsuz olarak erişmek için istemcisini oluşturun ve `Begin[Operation]` (örneğin,) öğesini çağırın `BeginAdd` ve aşağıdaki örnek kodda gösterildiği gibi bir geri çağırma işlevi belirtin.</span><span class="sxs-lookup"><span data-stu-id="ec57c-117">To access a service operation asynchronously, create the client and call the `Begin[Operation]` (for example, `BeginAdd`) and specify a callback function, as shown in the following sample code.</span></span>  
  
     [!code-csharp[C_How_To_CF_Async#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#3)]
     [!code-vb[C_How_To_CF_Async#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#3)]  
  
     <span data-ttu-id="ec57c-118">Geri çağırma işlevi yürütüldüğünde, istemci, `End<operation>` sonucu almak için (örneğin, `EndAdd` ) çağırır.</span><span class="sxs-lookup"><span data-stu-id="ec57c-118">When the callback function executes, the client calls `End<operation>` (for example, `EndAdd`) to retrieve the result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec57c-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="ec57c-119">Example</span></span>  

 <span data-ttu-id="ec57c-120">Önceki yordamda kullanılan istemci koduyla kullanılan hizmet, `ICalculator` aşağıdaki kodda gösterildiği gibi arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="ec57c-120">The service that is used with the client code that is used in the preceding procedure implements the `ICalculator` interface as shown in the following code.</span></span> <span data-ttu-id="ec57c-121">Hizmet tarafında, `Add` `Subtract` bir önceki istemci adımları istemcide zaman uyumsuz olarak çağrılsa bile, sözleşmenin ve işlemleri WINDOWS COMMUNICATION FOUNDATION (WCF) çalışma zamanına göre zaman uyumlu olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="ec57c-121">On the service side, the `Add` and `Subtract` operations of the contract are invoked synchronously by the Windows Communication Foundation (WCF) run time, even though the preceding client steps are invoked asynchronously on the client.</span></span> <span data-ttu-id="ec57c-122">`Multiply`Ve `Divide` işlemleri, istemci, zaman uyumlu olarak çağırsa bile hizmet tarafında zaman uyumsuz olarak hizmeti çağırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ec57c-122">The `Multiply` and `Divide` operations are used to invoke the service asynchronously on the service side, even if the client invokes them synchronously.</span></span> <span data-ttu-id="ec57c-123">Bu örnek, <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> özelliğini olarak ayarlar `true` .</span><span class="sxs-lookup"><span data-stu-id="ec57c-123">This example sets the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property to `true`.</span></span> <span data-ttu-id="ec57c-124">Bu özellik ayarı, .NET Framework zaman uyumsuz deseninin uygulanmasıyla birlikte, işlemi zaman uyumsuz olarak çağırmak için çalışma zamanına bildirir.</span><span class="sxs-lookup"><span data-stu-id="ec57c-124">This property setting, in combination with the implementation of the .NET Framework asynchronous pattern, tells the run time to invoke the operation asynchronously.</span></span>  
  
 [!code-csharp[C_How_To_CF_Async#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/service.cs#4)]
 [!code-vb[C_How_To_CF_Async#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/service.vb#4)]  
