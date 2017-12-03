---
title: "Nasıl yapılır: Akışı Etkinleştirme"
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
ms.assetid: 6ca2cf4b-c7a1-49d8-a79b-843a90556ba4
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ea506499cf6678beb51195654739f2537b98a188
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-enable-streaming"></a><span data-ttu-id="db1b0-102">Nasıl yapılır: Akışı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="db1b0-102">How to: Enable Streaming</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="db1b0-103">arabelleğe alınan veya akış aktarımları kullanarak iletiler gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="db1b0-103"> can send messages using either buffered or streamed transfers.</span></span> <span data-ttu-id="db1b0-104">Bir alıcı okumadan önce varsayılan arabelleğe aktarım modunda bir ileti tamamen teslim edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="db1b0-104">In the default buffered-transfer mode, a message must be completely delivered before a receiver can read it.</span></span> <span data-ttu-id="db1b0-105">Aktarım modunu akışında alıcı tamamen teslim edilmeden önce iletiyi işlemek başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="db1b0-105">In streaming transfer mode, the receiver can begin to process the message before it is completely delivered.</span></span> <span data-ttu-id="db1b0-106">Geçirilen bilgi uzun olduğunda ve seri olarak işlenebilen akış modu yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="db1b0-106">The streaming mode is useful when the information that is passed is lengthy and can be processed serially.</span></span> <span data-ttu-id="db1b0-107">Akış modu de, ileti tamamen arabelleğe çok büyük olduğunda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="db1b0-107">Streaming mode is also useful when the message is too large to be entirely buffered.</span></span>  
  
 <span data-ttu-id="db1b0-108">Akışını etkinleştirmek için tanımlamak `OperationContract` uygun şekilde ve aktarım düzeyinde akış etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="db1b0-108">To enable streaming, define the `OperationContract` appropriately and enable streaming at the transport level.</span></span>  
  
### <a name="to-stream-data"></a><span data-ttu-id="db1b0-109">Veri akışı</span><span class="sxs-lookup"><span data-stu-id="db1b0-109">To stream data</span></span>  
  
1.  <span data-ttu-id="db1b0-110">Veri akışı için `OperationContract` için hizmet iki gereksinimleri karşılaması gerekir:</span><span class="sxs-lookup"><span data-stu-id="db1b0-110">To stream data, the `OperationContract` for the service must satisfy two requirements:</span></span>  
  
    1.  <span data-ttu-id="db1b0-111">Veri akışı tutar parametresi yöntemi yalnızca parametresinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="db1b0-111">The parameter that holds the data to be streamed must be the only parameter in the method.</span></span> <span data-ttu-id="db1b0-112">Örneğin, giriş ileti akışını ise, işlemi tam olarak bir giriş parametresi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="db1b0-112">For example, if the input message is the one to be streamed, the operation must have exactly one input parameter.</span></span> <span data-ttu-id="db1b0-113">Benzer şekilde, çıktı ileti akışı, işlemi tam olarak bir çıkış parametresi veya dönüş değeri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="db1b0-113">Similarly, if the output message is to be streamed, the operation must have either exactly one output parameter or a return value.</span></span>  
  
    2.  <span data-ttu-id="db1b0-114">En az bir parametre ve dönüş değer türlerini olmalıdır ya da <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, veya <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="db1b0-114">At least one of the types of the parameter and return value must be either <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, or <xref:System.Xml.Serialization.IXmlSerializable>.</span></span>  
  
     <span data-ttu-id="db1b0-115">Bir sözleşme akış verileri için bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="db1b0-115">The following is an example of a contract for streamed data.</span></span>  
  
     [!code-csharp[c_HowTo_EnableStreaming#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#1)]
     [!code-vb[c_HowTo_EnableStreaming#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#1)]  
  
     <span data-ttu-id="db1b0-116">`GetStream` İşlemi bazı arabelleğe alınan girdi verisi olarak aldığı bir `string`, hangi arabelleğe alınıp ve döndürür bir `Stream`, akışı.</span><span class="sxs-lookup"><span data-stu-id="db1b0-116">The `GetStream` operation receives some buffered input data as a `string`, which is buffered, and returns a `Stream`, which is streamed.</span></span> <span data-ttu-id="db1b0-117">Buna karşılık `UploadStream` alır bir `Stream` (akışı) ve döndüren bir `bool` (arabelleğe).</span><span class="sxs-lookup"><span data-stu-id="db1b0-117">Conversely `UploadStream` takes in a `Stream` (streamed) and returns a `bool` (buffered).</span></span> <span data-ttu-id="db1b0-118">`EchoStream`alan ve döndüren `Stream` ve bir işlemin girişi örneğidir ve çıktı iletileri her ikisi de akışı.</span><span class="sxs-lookup"><span data-stu-id="db1b0-118">`EchoStream` takes and returns `Stream` and is an example of an operation whose input and output messages are both streamed.</span></span> <span data-ttu-id="db1b0-119">Son olarak, `GetReversedStream` hiç giriş alıp döndüren bir `Stream` (akış).</span><span class="sxs-lookup"><span data-stu-id="db1b0-119">Finally, `GetReversedStream` takes no inputs and returns a `Stream` (streamed).</span></span>  
  
2.  <span data-ttu-id="db1b0-120">Akış bağlamada etkinleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="db1b0-120">Streaming must be enabled on the binding.</span></span> <span data-ttu-id="db1b0-121">Belirlediğiniz bir `TransferMode` aşağıdaki değerlerden birini alabilir özelliği:</span><span class="sxs-lookup"><span data-stu-id="db1b0-121">You set a `TransferMode` property, which can take one of the following values:</span></span>  
  
    1.  <span data-ttu-id="db1b0-122">`Buffered`,</span><span class="sxs-lookup"><span data-stu-id="db1b0-122">`Buffered`,</span></span>  
  
    2.  <span data-ttu-id="db1b0-123">`Streamed`, her iki yönde akış iletişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="db1b0-123">`Streamed`, which enables streaming communication in both directions.</span></span>  
  
    3.  <span data-ttu-id="db1b0-124">`StreamedRequest`, istek yalnızca akış sağlar.</span><span class="sxs-lookup"><span data-stu-id="db1b0-124">`StreamedRequest`, which enables streaming the request only.</span></span>  
  
    4.  <span data-ttu-id="db1b0-125">`StreamedResponse`, yalnızca yanıtı akış sağlar.</span><span class="sxs-lookup"><span data-stu-id="db1b0-125">`StreamedResponse`, which enables streaming the response only.</span></span>  
  
     <span data-ttu-id="db1b0-126">`BasicHttpBinding` Sunan `TransferMode` yaptığı gibi bağlama özellikte `NetTcpBinding` ve `NetNamedPipeBinding`.</span><span class="sxs-lookup"><span data-stu-id="db1b0-126">The `BasicHttpBinding` exposes the `TransferMode` property on the binding, as does `NetTcpBinding` and `NetNamedPipeBinding`.</span></span> <span data-ttu-id="db1b0-127">`TransferMode` Özelliği de ayarlanabilir aktarım bağlama öğesi üzerindeki ve özel bir bağlama kullanılır.</span><span class="sxs-lookup"><span data-stu-id="db1b0-127">The `TransferMode` property can also be set on the transport binding element and used in a custom binding.</span></span>  
  
     <span data-ttu-id="db1b0-128">Aşağıdaki örnekler nasıl ayarlanacağını göstermektedir `TransferMode` kod hem yapılandırma dosyasını değiştirerek.</span><span class="sxs-lookup"><span data-stu-id="db1b0-128">The following samples show how to set `TransferMode` by code and by changing the configuration file.</span></span> <span data-ttu-id="db1b0-129">Her ikisi de ayarlayın örnekleri `maxReceivedMessageSize` cap iletilerin en fazla izin verilen boyutu yerleştirir 64 MB özelliğine alırsınız.</span><span class="sxs-lookup"><span data-stu-id="db1b0-129">The samples also both set the `maxReceivedMessageSize` property to 64 MB, which places a cap on the maximum allowable size of messages on receive.</span></span> <span data-ttu-id="db1b0-130">Varsayılan `maxReceivedMessageSize` genellikle senaryoları akış için çok düşük 64 KB ' tır.</span><span class="sxs-lookup"><span data-stu-id="db1b0-130">The default `maxReceivedMessageSize` is 64 KB, which is usually too low for streaming scenarios.</span></span> <span data-ttu-id="db1b0-131">Bu kota ayarı iletileri almak için uygulamanızı bekliyor en büyük boyutuna bağlı olarak uygun şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="db1b0-131">Set this quota setting as appropriate depending on the maximum size of messages your application expects to receive.</span></span> <span data-ttu-id="db1b0-132">Ayrıca `maxBufferSize` arabelleğe ve uygun şekilde ayarlanmış maksimum boyutu denetler.</span><span class="sxs-lookup"><span data-stu-id="db1b0-132">Also note that `maxBufferSize` controls the maximum size that is buffered, and set it appropriately.</span></span>  
  
    1.  <span data-ttu-id="db1b0-133">Aşağıdaki yapılandırma parçacığını örnekten ayarını gösterir `TransferMode` üzerinde akış özelliği `basicHttpBinding` ve özel HTTP bağlama.</span><span class="sxs-lookup"><span data-stu-id="db1b0-133">The following configuration snippet from the sample shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding.</span></span>  
  
         [!code-xml[c_HowTo_EnableStreaming#103](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/common/app.config#103)]   
  
    2.  <span data-ttu-id="db1b0-134">Aşağıdaki kod parçacığını ayarını gösterir `TransferMode` üzerinde akış özelliği `basicHttpBinding` ve özel HTTP bağlama.</span><span class="sxs-lookup"><span data-stu-id="db1b0-134">The following code snippet shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding.</span></span>  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#2)]
         [!code-vb[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#2)]  
  
    3.  <span data-ttu-id="db1b0-135">Aşağıdaki kod parçacığını ayarını gösterir `TransferMode` özel TCP bağlamada akış özelliği.</span><span class="sxs-lookup"><span data-stu-id="db1b0-135">The following code snippet shows setting the `TransferMode` property to streaming on a custom TCP binding.</span></span>  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#3)]
         [!code-vb[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#3)]  
  
3.  <span data-ttu-id="db1b0-136">İşlemleri `GetStream`, `UploadStream`, ve `EchoStream` tüm işlem doğrudan bir dosyadan veri gönderme veya bir dosyaya doğrudan alınan veri kaydetme.</span><span class="sxs-lookup"><span data-stu-id="db1b0-136">The operations `GetStream`, `UploadStream`, and `EchoStream` all deal with sending data directly from a file or saving received data directly to a file.</span></span> <span data-ttu-id="db1b0-137">Aşağıdaki kod içindir `GetStream`.</span><span class="sxs-lookup"><span data-stu-id="db1b0-137">The following code is for `GetStream`.</span></span>  
  
     [!code-csharp[c_HowTo_EnableStreaming#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#4)]
     [!code-vb[c_HowTo_EnableStreaming#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#4)]  
  
### <a name="writing-a-custom-stream"></a><span data-ttu-id="db1b0-138">Özel akış yazma</span><span class="sxs-lookup"><span data-stu-id="db1b0-138">Writing a custom stream</span></span>  
  
1.  <span data-ttu-id="db1b0-139">Gönderilen gibi bir veri akışı, her bir öbeğin üzerindeki özel işleme yapın veya alınan özel akış sınıfından türetilen <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="db1b0-139">To do special processing on each chunk of a data stream as it is being sent or received, derive a custom stream class from <xref:System.IO.Stream>.</span></span> <span data-ttu-id="db1b0-140">Özel akış örnek olarak, aşağıdaki kodu içeren bir `GetReversedStream` yöntemi ve `ReverseStream` sınıfı-.</span><span class="sxs-lookup"><span data-stu-id="db1b0-140">As an example of a custom stream, the following code contains a `GetReversedStream` method and a `ReverseStream` class-.</span></span>  
  
     <span data-ttu-id="db1b0-141">`GetReversedStream`oluşturur ve yeni bir örneğini döndürür `ReverseStream`.</span><span class="sxs-lookup"><span data-stu-id="db1b0-141">`GetReversedStream` creates and returns a new instance of `ReverseStream`.</span></span> <span data-ttu-id="db1b0-142">Sistem okur gibi gerçek işleme olur `ReverseStream` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="db1b0-142">The actual processing happens as the system reads from the `ReverseStream` object.</span></span> <span data-ttu-id="db1b0-143">`ReverseStream.Read` Yöntemi bayt bir öbek temel alınan dosyayı okur, bunları geri alır, ardından ters bayt döndürür.</span><span class="sxs-lookup"><span data-stu-id="db1b0-143">The `ReverseStream.Read` method reads a chunk of bytes from the underlying file, reverses them, then returns the reversed bytes.</span></span> <span data-ttu-id="db1b0-144">Bu yöntem, tüm dosya içeriği ters değil; bir kerede bir öbek bayt tersine çevirir.</span><span class="sxs-lookup"><span data-stu-id="db1b0-144">This method does not reverse the entire file content; it reverses one chunk of bytes at a time.</span></span> <span data-ttu-id="db1b0-145">Bu örnek nasıl içerik olarak akış işleme gerçekleştirebilirsiniz gösterir için okuma veya akıştan yazılır.</span><span class="sxs-lookup"><span data-stu-id="db1b0-145">This example shows how you can perform stream processing as the content is being read to or written from the stream.</span></span>  
  
     [!code-csharp[c_HowTo_EnableStreaming#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#2)]
     [!code-vb[c_HowTo_EnableStreaming#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="db1b0-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="db1b0-146">See Also</span></span>  
 [<span data-ttu-id="db1b0-147">Büyük veri ve akış</span><span class="sxs-lookup"><span data-stu-id="db1b0-147">Large Data and Streaming</span></span>](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)  
 [<span data-ttu-id="db1b0-148">Akış</span><span class="sxs-lookup"><span data-stu-id="db1b0-148">Stream</span></span>](../../../../docs/framework/wcf/samples/stream.md)
