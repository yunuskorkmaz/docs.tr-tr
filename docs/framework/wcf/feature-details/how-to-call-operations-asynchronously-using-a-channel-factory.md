---
title: "Nasıl yapılır: Kanal Fabrikası Kullanarak İşlemlere Zaman Uyumsuz Olarak Çağrı Yapma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: cc17dd47-b9ad-451c-a362-e36e0aac7ba0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8e0ef2dbd52e6628e7b784c50d2ce29306216772
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-call-operations-asynchronously-using-a-channel-factory"></a><span data-ttu-id="3022d-102">Nasıl yapılır: Kanal Fabrikası Kullanarak İşlemlere Zaman Uyumsuz Olarak Çağrı Yapma</span><span class="sxs-lookup"><span data-stu-id="3022d-102">How to: Call Operations Asynchronously Using a Channel Factory</span></span>
<span data-ttu-id="3022d-103">Bu konu, nasıl bir istemci bir hizmet işlemi zaman uyumsuz olarak kullanırken erişebilir kapsar bir <xref:System.ServiceModel.ChannelFactory%601>-tabanlı istemci.</span><span class="sxs-lookup"><span data-stu-id="3022d-103">This topic covers how a client can access a service operation asynchronously when using a <xref:System.ServiceModel.ChannelFactory%601>-based client application.</span></span> <span data-ttu-id="3022d-104">(Kullanırken bir <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> olay tabanlı zaman uyumsuz çağırma model kullanabileceğiniz hizmetini çağırmak için nesne.</span><span class="sxs-lookup"><span data-stu-id="3022d-104">(When using a <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> object to invoke a service you can use the event-driven asynchronous calling model.</span></span> <span data-ttu-id="3022d-105">Daha fazla bilgi için bkz: [nasıl yapılır: hizmet işlemlerini zaman uyumsuz çağrı](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="3022d-105">For more information, see [How to: Call Service Operations Asynchronously](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span> <span data-ttu-id="3022d-106">Olay tabanlı zaman uyumsuz çağırma modeli hakkında daha fazla bilgi için bkz: [birden çok iş parçacıklı programlama olay tabanlı zaman uyumsuz desen ile](../../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md).)</span><span class="sxs-lookup"><span data-stu-id="3022d-106">For more information about the event-based asynchronous calling model, see [Multithreaded Programming with the Event-based Asynchronous Pattern](../../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md).)</span></span>  
  
 <span data-ttu-id="3022d-107">Bu konuda hizmeti uygulayan `ICalculator` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="3022d-107">The service in this topic implements the `ICalculator` interface.</span></span> <span data-ttu-id="3022d-108">İstemci bu arabirimde işlemlerini zaman uyumsuz olarak işlemlerini ister anlamına gelir çağırabilirsiniz `Add` iki yöntem bölme `BeginAdd` ve `EndAdd`, eski biri çağrı başlatır ve ikincisi biri alır sonucu İşlem tamamlandığında.</span><span class="sxs-lookup"><span data-stu-id="3022d-108">The client can call the operations on this interface asynchronously, which means that operations like `Add` are split into two methods, `BeginAdd` and `EndAdd`, the former of which initiates the call and the latter of which retrieves the result when the operation completes.</span></span> <span data-ttu-id="3022d-109">Bir işlem zaman uyumsuz olarak bir hizmet olarak uygulamak nasıl gösteren bir örnek için bkz: [nasıl yapılır: zaman uyumsuz bir hizmet işlemi uygulama](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span><span class="sxs-lookup"><span data-stu-id="3022d-109">For an example showing how to implement an operation asynchronously in a service, see [How to: Implement an Asynchronous Service Operation](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span></span> <span data-ttu-id="3022d-110">Zaman uyumlu ve zaman uyumsuz işlemler hakkında daha fazla ayrıntı için bkz: [zaman uyumlu ve zaman uyumsuz işlemleri](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="3022d-110">For details about synchronous and asynchronous operations, see [Synchronous and Asynchronous Operations](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="3022d-111">Yordam</span><span class="sxs-lookup"><span data-stu-id="3022d-111">Procedure</span></span>  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="3022d-112">WCF Hizmeti işlemlerini zaman uyumsuz olarak çağırmak için</span><span class="sxs-lookup"><span data-stu-id="3022d-112">To call WCF service operations asynchronously</span></span>  
  
1.  <span data-ttu-id="3022d-113">Çalıştırma [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ile aracı `/async` seçenek aşağıdaki komutta gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="3022d-113">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool with the `/async` option as shown in the following command.</span></span>  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a  
    ```  
  
     <span data-ttu-id="3022d-114">Bu işlem için hizmet sözleşmesini zaman uyumsuz istemci sürümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3022d-114">This generates an asynchronous client version of the service contract for the operation.</span></span>  
  
2.  <span data-ttu-id="3022d-115">Zaman uyumsuz işlemi aşağıdaki örnek kodda gösterildiği gibi tamamlandığında çağrılacak bir geri çağırma işlevini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3022d-115">Create a callback function to be called when the asynchronous operation is complete, as shown in the following sample code.</span></span>  
  
     [!code-csharp[C_How_To_CF_Async#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#2)]
     [!code-vb[C_How_To_CF_Async#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#2)]  
  
3.  <span data-ttu-id="3022d-116">Bir hizmet işlemi zaman uyumsuz olarak erişmek için istemci ve çağrı oluşturma `Begin[Operation]` (örneğin, `BeginAdd`) ve aşağıdaki örnek kodda gösterildiği gibi bir geri çağırma işlevi belirtin.</span><span class="sxs-lookup"><span data-stu-id="3022d-116">To access a service operation asynchronously, create the client and call the `Begin[Operation]` (for example, `BeginAdd`) and specify a callback function, as shown in the following sample code.</span></span>  
  
     [!code-csharp[C_How_To_CF_Async#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#3)]
     [!code-vb[C_How_To_CF_Async#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#3)]  
  
     <span data-ttu-id="3022d-117">Geri çağırma işlevi yürütüldüğünde, istemcinin çağıran `End<operation>` (örneğin, `EndAdd`) sonucu alınamadı.</span><span class="sxs-lookup"><span data-stu-id="3022d-117">When the callback function executes, the client calls `End<operation>` (for example, `EndAdd`) to retrieve the result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3022d-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="3022d-118">Example</span></span>  
 <span data-ttu-id="3022d-119">Önceki yordamda kullanılan istemci kodu ile birlikte kullanılan hizmeti uygulayan `ICalculator` arabirimi aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="3022d-119">The service that is used with the client code that is used in the preceding procedure implements the `ICalculator` interface as shown in the following code.</span></span> <span data-ttu-id="3022d-120">Hizmet tarafında `Add` ve `Subtract` sözleşmenin işlemleri zaman uyumlu olarak göre çağrılır [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] önceki istemci adımları istemcide zaman uyumsuz olarak çağrılır olsa da, çalıştırma.</span><span class="sxs-lookup"><span data-stu-id="3022d-120">On the service side, the `Add` and `Subtract` operations of the contract are invoked synchronously by the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] run time, even though the preceding client steps are invoked asynchronously on the client.</span></span> <span data-ttu-id="3022d-121">`Multiply` Ve `Divide` işlemleri kullanılan zaman uyumsuz olarak hizmet tarafında hizmetini çağırmak için bile istemci bunları zaman uyumlu olarak çağırır.</span><span class="sxs-lookup"><span data-stu-id="3022d-121">The `Multiply` and `Divide` operations are used to invoke the service asynchronously on the service side, even if the client invokes them synchronously.</span></span> <span data-ttu-id="3022d-122">Bu örnek ayarlar <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="3022d-122">This example sets the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property to `true`.</span></span> <span data-ttu-id="3022d-123">Uygulaması ile birlikte bu özellik ayarı [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zaman uyumsuz desen işlemi zaman uyumsuz olarak çağırmak için çalışma süresi söyler.</span><span class="sxs-lookup"><span data-stu-id="3022d-123">This property setting, in combination with the implementation of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] asynchronous pattern, tells the run time to invoke the operation asynchronously.</span></span>  
  
 [!code-csharp[C_How_To_CF_Async#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/service.cs#4)]
 [!code-vb[C_How_To_CF_Async#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/service.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="3022d-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3022d-124">See Also</span></span>  
 [<span data-ttu-id="3022d-125">Hizmet sözleşmesi: Zaman uyumsuz örnek</span><span class="sxs-lookup"><span data-stu-id="3022d-125">Service Contract: Asynchronous Sample</span></span>](http://msdn.microsoft.com/en-us/833db946-f511-4f64-a26f-2759a11217c7)
