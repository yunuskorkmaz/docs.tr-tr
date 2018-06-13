---
title: 'Nasıl yapılır: WCF Hizmeti İşlemlerini Zaman Uyumsuz Olarak Çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
ms.openlocfilehash: 8058f0fac8a0401f72f84e2d2e91c28c7e46d1e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493369"
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="bd1eb-102">Nasıl yapılır: WCF Hizmeti İşlemlerini Zaman Uyumsuz Olarak Çağırma</span><span class="sxs-lookup"><span data-stu-id="bd1eb-102">How to: Call WCF Service Operations Asynchronously</span></span>
<span data-ttu-id="bd1eb-103">Bu konu, nasıl bir istemci bir hizmet işlemi zaman uyumsuz olarak erişebilir kapsar.</span><span class="sxs-lookup"><span data-stu-id="bd1eb-103">This topic covers how a client can access a service operation asynchronously.</span></span> <span data-ttu-id="bd1eb-104">Bu konuda hizmeti uygulayan `ICalculator` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="bd1eb-104">The service in this topic implements the `ICalculator` interface.</span></span> <span data-ttu-id="bd1eb-105">İstemci bu arabirimde işlemleri olay tabanlı zaman uyumsuz çağırma modelini kullanarak zaman uyumsuz olarak çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd1eb-105">The client can call the operations on this interface asynchronously by using the event-driven asynchronous calling model.</span></span> <span data-ttu-id="bd1eb-106">(Olay tabanlı zaman uyumsuz çağırma modeli hakkında daha fazla bilgi için bkz: [birden çok iş parçacıklı programlama olay tabanlı zaman uyumsuz desen ile](http://go.microsoft.com/fwlink/?LinkId=248184)).</span><span class="sxs-lookup"><span data-stu-id="bd1eb-106">(For more information about the event-based asynchronous calling model, see [Multithreaded Programming with the Event-based Asynchronous Pattern](http://go.microsoft.com/fwlink/?LinkId=248184)).</span></span> <span data-ttu-id="bd1eb-107">Bir işlem zaman uyumsuz olarak bir hizmet olarak uygulamak gösteren örnek için bkz: [nasıl yapılır: zaman uyumsuz bir hizmet işlemi uygulama](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span><span class="sxs-lookup"><span data-stu-id="bd1eb-107">For an example that shows how to implement an operation asynchronously in a service, see [How to: Implement an Asynchronous Service Operation](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span></span> <span data-ttu-id="bd1eb-108">Zaman uyumlu ve zaman uyumsuz işlemler hakkında daha fazla bilgi için bkz: [zaman uyumlu ve zaman uyumsuz işlemleri](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="bd1eb-108">For more information about synchronous and asynchronous operations, see [Synchronous and Asynchronous Operations](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd1eb-109">Olay tabanlı zaman uyumsuz çağırma modeli kullanılırken desteklenmeyen bir <xref:System.ServiceModel.ChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="bd1eb-109">The event-driven asynchronous calling model is not supported when using a <xref:System.ServiceModel.ChannelFactory%601>.</span></span> <span data-ttu-id="bd1eb-110">Kullanarak zaman uyumsuz çağrıları yapma hakkında bilgi için <xref:System.ServiceModel.ChannelFactory%601>, bkz: [nasıl yapılır: çağrı işlemlerini zaman uyumsuz olarak kullanarak bir kanal fabrikası](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span><span class="sxs-lookup"><span data-stu-id="bd1eb-110">For information about making asynchronous calls using the <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="bd1eb-111">Yordam</span><span class="sxs-lookup"><span data-stu-id="bd1eb-111">Procedure</span></span>  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="bd1eb-112">WCF Hizmeti işlemlerini zaman uyumsuz olarak çağırmak için</span><span class="sxs-lookup"><span data-stu-id="bd1eb-112">To call WCF service operations asynchronously</span></span>  
  
1.  <span data-ttu-id="bd1eb-113">Çalıştırma [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) her ikisi de aracıyla `/async` ve `/tcv:Version35` komutu seçenekleri birlikte aşağıdaki komutta gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="bd1eb-113">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool with both the `/async` and the `/tcv:Version35` command options together as shown in the following command.</span></span>  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     <span data-ttu-id="bd1eb-114">Bu, zaman uyumlu ve standart temsilci tabanlı zaman uyumsuz işlemlerin yanı sıra, içeren bir WCF istemcisi sınıf oluşturur:</span><span class="sxs-lookup"><span data-stu-id="bd1eb-114">This generates, in addition to the synchronous and standard delegate-based asynchronous operations, a WCF client class that contains:</span></span>  
  
    -   <span data-ttu-id="bd1eb-115">İki <`operationName` > `Async` işlemleri için olay tabanlı zaman uyumsuz çağırma yaklaşımı kullanın.</span><span class="sxs-lookup"><span data-stu-id="bd1eb-115">Two <`operationName`>`Async` operations for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="bd1eb-116">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="bd1eb-116">For example:</span></span>  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    -   <span data-ttu-id="bd1eb-117">İşlem tamamlandı olayları formun <`operationName` > `Completed` olay tabanlı zaman uyumsuz çağırma yaklaşımı ile kullanım için.</span><span class="sxs-lookup"><span data-stu-id="bd1eb-117">Operation completed events of the form <`operationName`>`Completed` for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="bd1eb-118">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="bd1eb-118">For example:</span></span>  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    -   <span data-ttu-id="bd1eb-119"><xref:System.EventArgs?displayProperty=nameWithType> Her bir işlemin türleri (form <`operationName`>`CompletedEventArgs`) olay tabanlı zaman uyumsuz çağırma yaklaşımı ile kullanım için.</span><span class="sxs-lookup"><span data-stu-id="bd1eb-119"><xref:System.EventArgs?displayProperty=nameWithType> types for each operation (of the form <`operationName`>`CompletedEventArgs`) for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="bd1eb-120">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="bd1eb-120">For example:</span></span>  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2.  <span data-ttu-id="bd1eb-121">Arama uygulamasında zaman uyumsuz işlemi aşağıdaki örnek kodda gösterildiği gibi tamamlandığında çağrılacak bir geri çağırma yöntemi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bd1eb-121">In the calling application, create a callback method to be called when the asynchronous operation is complete, as shown in the following sample code.</span></span>  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3.  <span data-ttu-id="bd1eb-122">Yeni genel kullanma işlemi çağırmadan önce <xref:System.EventHandler%601?displayProperty=nameWithType> türü <`operationName` > `EventArgs` (önceki adımda oluşturulan) işleyici yöntemi eklemek için <`operationName` > `Completed` olay.</span><span class="sxs-lookup"><span data-stu-id="bd1eb-122">Prior to calling the operation, use a new generic <xref:System.EventHandler%601?displayProperty=nameWithType> of type <`operationName`>`EventArgs` to add the handler method (created in the preceding step) to the <`operationName`>`Completed` event.</span></span> <span data-ttu-id="bd1eb-123">' I çağırın <`operationName` > `Async` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bd1eb-123">Then call the <`operationName`>`Async` method.</span></span> <span data-ttu-id="bd1eb-124">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="bd1eb-124">For example:</span></span>  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="bd1eb-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="bd1eb-125">Example</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd1eb-126">Olay tabanlı zaman uyumsuz modeli için tasarım yönergeleri birden fazla değer döndürülürse, tek bir değer olarak döndürülen durum `Result` özelliği ve diğerleri döndürülür özellikleri olarak üzerinde <xref:System.EventArgs> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="bd1eb-126">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="bd1eb-127">Bunun bir sonucu olduğundan, bu, istemci olay tabanlı zaman uyumsuz komut seçeneklerini kullanarak meta verilerini alır ve birden fazla değer, varsayılan işlemi döndürürse <xref:System.EventArgs> nesnesi döndüren bir değer olarak `Result` özelliği ve geri kalan özelliklerini <xref:System.EventArgs> nesnesi. İleti nesnesi olarak almak istiyorsanız `Result` özelliği ve bu nesne üzerinde özellikleri kullanma gibi döndürülen değerlere sahip `/messageContract` komut seçeneği.</span><span class="sxs-lookup"><span data-stu-id="bd1eb-127">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the `/messageContract` command option.</span></span> <span data-ttu-id="bd1eb-128">Bu olarak yanıt iletisi döndüren bir imza oluşturur `Result` özellikte <xref:System.EventArgs> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="bd1eb-128">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="bd1eb-129">Tüm iç dönüş değerleri yanıt iletisi nesnesi sonra özellikleridir.</span><span class="sxs-lookup"><span data-stu-id="bd1eb-129">All internal return values are then properties of the response message object.</span></span>  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="bd1eb-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bd1eb-130">See Also</span></span>  
 [<span data-ttu-id="bd1eb-131">Nasıl yapılır: Zaman Uyumsuz Bir Hizmet İşlemi Uygulama</span><span class="sxs-lookup"><span data-stu-id="bd1eb-131">How to: Implement an Asynchronous Service Operation</span></span>](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)
