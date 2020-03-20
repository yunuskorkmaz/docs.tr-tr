---
title: 'Nasıl yapılır: Akışı Etkinleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6ca2cf4b-c7a1-49d8-a79b-843a90556ba4
ms.openlocfilehash: 1d1eaa1ebf41ef86478dda795b3b199239cd37b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184940"
---
# <a name="how-to-enable-streaming"></a><span data-ttu-id="da4ed-102">Nasıl yapılır: Akışı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="da4ed-102">How to: Enable Streaming</span></span>
<span data-ttu-id="da4ed-103">Windows Communication Foundation (WCF), arabelleğe alınan veya akışlı aktarımları kullanarak ileti gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="da4ed-103">Windows Communication Foundation (WCF) can send messages using either buffered or streamed transfers.</span></span> <span data-ttu-id="da4ed-104">Varsayılan arabelleğe alınan aktarım modunda, bir iletinin bir alıcının okuyabilmesi için tamamen teslim edilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="da4ed-104">In the default buffered-transfer mode, a message must be completely delivered before a receiver can read it.</span></span> <span data-ttu-id="da4ed-105">Akış aktarım modunda, alıcı iletiyi tamamen teslim edilmeden önce işlemeye başlayabilir.</span><span class="sxs-lookup"><span data-stu-id="da4ed-105">In streaming transfer mode, the receiver can begin to process the message before it is completely delivered.</span></span> <span data-ttu-id="da4ed-106">Akış modu, geçirilen bilgiler uzun olduğunda ve seri olarak işlenebilirse yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="da4ed-106">The streaming mode is useful when the information that is passed is lengthy and can be processed serially.</span></span> <span data-ttu-id="da4ed-107">Akış modu, ileti tamamen arabelleğe alınamayacak kadar büyükolduğunda da kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="da4ed-107">Streaming mode is also useful when the message is too large to be entirely buffered.</span></span>  
  
 <span data-ttu-id="da4ed-108">Akışı etkinleştirmek için, uygun şekilde tanımlayın `OperationContract` ve aktarım düzeyinde akışı etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="da4ed-108">To enable streaming, define the `OperationContract` appropriately and enable streaming at the transport level.</span></span>  
  
### <a name="to-stream-data"></a><span data-ttu-id="da4ed-109">Veri akışı için</span><span class="sxs-lookup"><span data-stu-id="da4ed-109">To stream data</span></span>  
  
1. <span data-ttu-id="da4ed-110">Veri akışı için, hizmet `OperationContract` için iki gereksinimi karşılamalıdır:</span><span class="sxs-lookup"><span data-stu-id="da4ed-110">To stream data, the `OperationContract` for the service must satisfy two requirements:</span></span>  
  
    1. <span data-ttu-id="da4ed-111">Akışlanacak verileri tutan parametre yöntemdeki tek parametre olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="da4ed-111">The parameter that holds the data to be streamed must be the only parameter in the method.</span></span> <span data-ttu-id="da4ed-112">Örneğin, giriş iletisi akış için bir işlem varsa, işlem tam olarak bir giriş parametresi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="da4ed-112">For example, if the input message is the one to be streamed, the operation must have exactly one input parameter.</span></span> <span data-ttu-id="da4ed-113">Benzer şekilde, çıktı iletisi akış olacaksa, işlemin tam olarak bir çıkış parametresi veya bir iade değeri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="da4ed-113">Similarly, if the output message is to be streamed, the operation must have either exactly one output parameter or a return value.</span></span>  
  
    2. <span data-ttu-id="da4ed-114">Parametre ve iade değeri türlerinden en az <xref:System.IO.Stream>biri <xref:System.ServiceModel.Channels.Message>, <xref:System.Xml.Serialization.IXmlSerializable>, veya .</span><span class="sxs-lookup"><span data-stu-id="da4ed-114">At least one of the types of the parameter and return value must be either <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, or <xref:System.Xml.Serialization.IXmlSerializable>.</span></span>  
  
     <span data-ttu-id="da4ed-115">Aşağıda, akışlı veriler için bir sözleşme örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="da4ed-115">The following is an example of a contract for streamed data.</span></span>  
  
     [!code-csharp[c_HowTo_EnableStreaming#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#1)]
     [!code-vb[c_HowTo_EnableStreaming#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#1)]  
  
     <span data-ttu-id="da4ed-116">İşlem, `GetStream` arabelleğe alınan bazı arabelleğe alınan giriş verilerini `string`, `Stream`arabelleğe alınan bir , olarak alır ve akışlı bir , döndürür.</span><span class="sxs-lookup"><span data-stu-id="da4ed-116">The `GetStream` operation receives some buffered input data as a `string`, which is buffered, and returns a `Stream`, which is streamed.</span></span> <span data-ttu-id="da4ed-117">Tersine `UploadStream` bir `Stream` (akış) alır ve `bool` bir (arabelleğe alındı) döndürür.</span><span class="sxs-lookup"><span data-stu-id="da4ed-117">Conversely `UploadStream` takes in a `Stream` (streamed) and returns a `bool` (buffered).</span></span> <span data-ttu-id="da4ed-118">`EchoStream`alır ve `Stream` döndürür ve giriş ve çıktı iletileri hem akış lı bir işlem örneğidir.</span><span class="sxs-lookup"><span data-stu-id="da4ed-118">`EchoStream` takes and returns `Stream` and is an example of an operation whose input and output messages are both streamed.</span></span> <span data-ttu-id="da4ed-119">Son `GetReversedStream` olarak, hiçbir giriş `Stream` alır ve bir (akış) döndürür.</span><span class="sxs-lookup"><span data-stu-id="da4ed-119">Finally, `GetReversedStream` takes no inputs and returns a `Stream` (streamed).</span></span>  
  
2. <span data-ttu-id="da4ed-120">Bağlamada akış etkinleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="da4ed-120">Streaming must be enabled on the binding.</span></span> <span data-ttu-id="da4ed-121">Aşağıdaki değerlerden birini alabilecek bir `TransferMode` özellik ayarlarsınız:</span><span class="sxs-lookup"><span data-stu-id="da4ed-121">You set a `TransferMode` property, which can take one of the following values:</span></span>  
  
    1. <span data-ttu-id="da4ed-122">`Buffered`,</span><span class="sxs-lookup"><span data-stu-id="da4ed-122">`Buffered`,</span></span>  
  
    2. <span data-ttu-id="da4ed-123">`Streamed`, her iki yönde de iletişim akışı sağlar.</span><span class="sxs-lookup"><span data-stu-id="da4ed-123">`Streamed`, which enables streaming communication in both directions.</span></span>  
  
    3. <span data-ttu-id="da4ed-124">`StreamedRequest`, yalnızca isteği akışı sağlar.</span><span class="sxs-lookup"><span data-stu-id="da4ed-124">`StreamedRequest`, which enables streaming the request only.</span></span>  
  
    4. <span data-ttu-id="da4ed-125">`StreamedResponse`, yalnızca yanıtAkışını sağlar.</span><span class="sxs-lookup"><span data-stu-id="da4ed-125">`StreamedResponse`, which enables streaming the response only.</span></span>  
  
     <span data-ttu-id="da4ed-126">Bağlama `BasicHttpBinding` özelliğini `TransferMode` ortaya çıkarır, yaptığı `NetTcpBinding` `NetNamedPipeBinding`gibi ve .</span><span class="sxs-lookup"><span data-stu-id="da4ed-126">The `BasicHttpBinding` exposes the `TransferMode` property on the binding, as does `NetTcpBinding` and `NetNamedPipeBinding`.</span></span> <span data-ttu-id="da4ed-127">Özellik, `TransferMode` aktarım bağlama öğesi üzerinde de ayarlanabilir ve özel bir bağlama da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="da4ed-127">The `TransferMode` property can also be set on the transport binding element and used in a custom binding.</span></span>  
  
     <span data-ttu-id="da4ed-128">Aşağıdaki örnekler, koda `TransferMode` göre ve yapılandırma dosyasını değiştirerek nasıl ayarlanır gösterin.</span><span class="sxs-lookup"><span data-stu-id="da4ed-128">The following samples show how to set `TransferMode` by code and by changing the configuration file.</span></span> <span data-ttu-id="da4ed-129">Örneklerin her ikisi `maxReceivedMessageSize` de özelliği 64 MB olarak ayarlar ve bu da alınan iletilerin izin verilen maksimum boyutuna bir kapak yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="da4ed-129">The samples also both set the `maxReceivedMessageSize` property to 64 MB, which places a cap on the maximum allowable size of messages on receive.</span></span> <span data-ttu-id="da4ed-130">Varsayılan `maxReceivedMessageSize` 64 KB, genellikle çok düşük akış senaryoları için.</span><span class="sxs-lookup"><span data-stu-id="da4ed-130">The default `maxReceivedMessageSize` is 64 KB, which is usually too low for streaming scenarios.</span></span> <span data-ttu-id="da4ed-131">Bu kota ayarını, uygulamanızın almayı beklediği maksimum ileti boyutuna bağlı olarak uygun şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="da4ed-131">Set this quota setting as appropriate depending on the maximum size of messages your application expects to receive.</span></span> <span data-ttu-id="da4ed-132">Arabelleğe `maxBufferSize` alınan maksimum boyutu denetler ve uygun şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="da4ed-132">Also note that `maxBufferSize` controls the maximum size that is buffered, and set it appropriately.</span></span>  
  
    1. <span data-ttu-id="da4ed-133">Örnekten aşağıdaki yapılandırma parçacığı, `TransferMode` özelliği akışa `basicHttpBinding` ve özel bir HTTP bağlamaya ayarlayışgösterir.</span><span class="sxs-lookup"><span data-stu-id="da4ed-133">The following configuration snippet from the sample shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding.</span></span>  
  
         [!code-xml[c_HowTo_EnableStreaming#103](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/common/app.config#103)]
  
    2. <span data-ttu-id="da4ed-134">Aşağıdaki kod snippet `TransferMode` `basicHttpBinding` ve özel bir HTTP bağlama üzerinde akış özelliği ayarı gösterir.</span><span class="sxs-lookup"><span data-stu-id="da4ed-134">The following code snippet shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding.</span></span>  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#2)]
         [!code-vb[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#2)]  
  
    3. <span data-ttu-id="da4ed-135">Aşağıdaki kod snippet özel `TransferMode` bir TCP bağlama üzerinde akış özelliği ayarı gösterir.</span><span class="sxs-lookup"><span data-stu-id="da4ed-135">The following code snippet shows setting the `TransferMode` property to streaming on a custom TCP binding.</span></span>  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#3)]
         [!code-vb[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#3)]  
  
3. <span data-ttu-id="da4ed-136">İşlemler `GetStream` `UploadStream`ve `EchoStream` tüm işlemler, doğrudan bir dosyadan veri gönderme veya alınan verileri doğrudan bir dosyaya kaydetme ile ilgilenir.</span><span class="sxs-lookup"><span data-stu-id="da4ed-136">The operations `GetStream`, `UploadStream`, and `EchoStream` all deal with sending data directly from a file or saving received data directly to a file.</span></span> <span data-ttu-id="da4ed-137">Aşağıdaki kod `GetStream`.</span><span class="sxs-lookup"><span data-stu-id="da4ed-137">The following code is for `GetStream`.</span></span>  
  
     [!code-csharp[c_HowTo_EnableStreaming#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#4)]
     [!code-vb[c_HowTo_EnableStreaming#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#4)]  
  
### <a name="writing-a-custom-stream"></a><span data-ttu-id="da4ed-138">Özel akış yazma</span><span class="sxs-lookup"><span data-stu-id="da4ed-138">Writing a custom stream</span></span>  
  
1. <span data-ttu-id="da4ed-139">Bir veri akışının gönderildiği veya alındığı her yığın da özel işleme yapmak için, 'den <xref:System.IO.Stream>özel bir akış sınıfı türetmek.</span><span class="sxs-lookup"><span data-stu-id="da4ed-139">To do special processing on each chunk of a data stream as it is being sent or received, derive a custom stream class from <xref:System.IO.Stream>.</span></span> <span data-ttu-id="da4ed-140">Özel bir akış örneği olarak, aşağıdaki `GetReversedStream` kod bir `ReverseStream` yöntem ve bir sınıf içerir.</span><span class="sxs-lookup"><span data-stu-id="da4ed-140">As an example of a custom stream, the following code contains a `GetReversedStream` method and a `ReverseStream` class-.</span></span>  
  
     <span data-ttu-id="da4ed-141">`GetReversedStream`yeni bir örnek oluşturur `ReverseStream`ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="da4ed-141">`GetReversedStream` creates and returns a new instance of `ReverseStream`.</span></span> <span data-ttu-id="da4ed-142">Gerçek işleme, sistem `ReverseStream` nesneden okurken gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="da4ed-142">The actual processing happens as the system reads from the `ReverseStream` object.</span></span> <span data-ttu-id="da4ed-143">Yöntem, `ReverseStream.Read` alttaki dosyadan bayt bir yığın okur, bunları tersine çevirir ve ters bayt döndürür.</span><span class="sxs-lookup"><span data-stu-id="da4ed-143">The `ReverseStream.Read` method reads a chunk of bytes from the underlying file, reverses them, then returns the reversed bytes.</span></span> <span data-ttu-id="da4ed-144">Bu yöntem, dosya içeriğinin tamamını tersine çevirmez; bir seferde bir bayt parçasını tersine çevirir.</span><span class="sxs-lookup"><span data-stu-id="da4ed-144">This method does not reverse the entire file content; it reverses one chunk of bytes at a time.</span></span> <span data-ttu-id="da4ed-145">Bu örnek, içerik akışa okunurken veya akıştan yazılırken akış işlemeyi nasıl gerçekleştirebileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="da4ed-145">This example shows how you can perform stream processing as the content is being read to or written from the stream.</span></span>  
  
     [!code-csharp[c_HowTo_EnableStreaming#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#2)]
     [!code-vb[c_HowTo_EnableStreaming#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="da4ed-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da4ed-146">See also</span></span>

- [<span data-ttu-id="da4ed-147">Büyük Veriler ve Akış Yapma</span><span class="sxs-lookup"><span data-stu-id="da4ed-147">Large Data and Streaming</span></span>](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)
- [<span data-ttu-id="da4ed-148">Akış</span><span class="sxs-lookup"><span data-stu-id="da4ed-148">Stream</span></span>](../../../../docs/framework/wcf/samples/stream.md)
