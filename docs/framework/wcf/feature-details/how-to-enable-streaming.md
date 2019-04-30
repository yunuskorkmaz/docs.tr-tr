---
title: 'Nasıl yapılır: Akışı Etkinleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6ca2cf4b-c7a1-49d8-a79b-843a90556ba4
ms.openlocfilehash: 0d8428487c3c320a634914b99219e23befb70d55
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773028"
---
# <a name="how-to-enable-streaming"></a><span data-ttu-id="b7e72-102">Nasıl yapılır: Akışı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="b7e72-102">How to: Enable Streaming</span></span>
<span data-ttu-id="b7e72-103">Windows Communication Foundation (WCF) iletilerini arabelleğe alınan ya da akış aktarımları kullanarak gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7e72-103">Windows Communication Foundation (WCF) can send messages using either buffered or streamed transfers.</span></span> <span data-ttu-id="b7e72-104">Bir alıcı okumadan önce varsayılan arabelleğe alınan aktarım modunda bir ileti tamamen teslim edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="b7e72-104">In the default buffered-transfer mode, a message must be completely delivered before a receiver can read it.</span></span> <span data-ttu-id="b7e72-105">Aktarım modunu akışında alıcı tamamen teslim edilmeden önce iletiyi işlemeye başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7e72-105">In streaming transfer mode, the receiver can begin to process the message before it is completely delivered.</span></span> <span data-ttu-id="b7e72-106">Akış modunda iletilen bilgiler uzun ve seri olarak işlenebilecek yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="b7e72-106">The streaming mode is useful when the information that is passed is lengthy and can be processed serially.</span></span> <span data-ttu-id="b7e72-107">Akış modunda de, ileti tamamen arabelleğe çok büyük olduğunda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="b7e72-107">Streaming mode is also useful when the message is too large to be entirely buffered.</span></span>  
  
 <span data-ttu-id="b7e72-108">Akışını etkinleştirmek için tanımladığınız `OperationContract` uygun şekilde ve akış taşıma düzeyinde etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="b7e72-108">To enable streaming, define the `OperationContract` appropriately and enable streaming at the transport level.</span></span>  
  
### <a name="to-stream-data"></a><span data-ttu-id="b7e72-109">Akış verileri</span><span class="sxs-lookup"><span data-stu-id="b7e72-109">To stream data</span></span>  
  
1. <span data-ttu-id="b7e72-110">Veri akışı `OperationContract` için hizmeti iki gereksinimleri karşılaması gerekir:</span><span class="sxs-lookup"><span data-stu-id="b7e72-110">To stream data, the `OperationContract` for the service must satisfy two requirements:</span></span>  
  
    1. <span data-ttu-id="b7e72-111">Akışla verileri tutan parametresi, yöntemin tek parametre olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b7e72-111">The parameter that holds the data to be streamed must be the only parameter in the method.</span></span> <span data-ttu-id="b7e72-112">Örneğin, giriş iletisine akışla birine ise, işlemi tam olarak bir girdi parametreniz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b7e72-112">For example, if the input message is the one to be streamed, the operation must have exactly one input parameter.</span></span> <span data-ttu-id="b7e72-113">Benzer şekilde, çıktı iletisi akışını ise işlemi tam olarak bir çıkış parametresi ya da dönüş değeri olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7e72-113">Similarly, if the output message is to be streamed, the operation must have either exactly one output parameter or a return value.</span></span>  
  
    2. <span data-ttu-id="b7e72-114">En az bir parametre ve dönüş değeri türlerini olmalıdır ya da <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, veya <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="b7e72-114">At least one of the types of the parameter and return value must be either <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, or <xref:System.Xml.Serialization.IXmlSerializable>.</span></span>  
  
     <span data-ttu-id="b7e72-115">Akış veri sözleşme örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b7e72-115">The following is an example of a contract for streamed data.</span></span>  
  
     [!code-csharp[c_HowTo_EnableStreaming#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#1)]
     [!code-vb[c_HowTo_EnableStreaming#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#1)]  
  
     <span data-ttu-id="b7e72-116">`GetStream` İşlemi arabelleğe alınan bazı girdi verisi olarak aldığı bir `string`, arabelleğe alınıp ve döndürür bir `Stream`, hangi akış.</span><span class="sxs-lookup"><span data-stu-id="b7e72-116">The `GetStream` operation receives some buffered input data as a `string`, which is buffered, and returns a `Stream`, which is streamed.</span></span> <span data-ttu-id="b7e72-117">Buna karşılık `UploadStream` alır bir `Stream` (akış) ve döndüren bir `bool` (arabelleğe).</span><span class="sxs-lookup"><span data-stu-id="b7e72-117">Conversely `UploadStream` takes in a `Stream` (streamed) and returns a `bool` (buffered).</span></span> <span data-ttu-id="b7e72-118">`EchoStream` alan ve döndüren `Stream` işlem girişi örneğidir ve çıkış iletileri hem de akış.</span><span class="sxs-lookup"><span data-stu-id="b7e72-118">`EchoStream` takes and returns `Stream` and is an example of an operation whose input and output messages are both streamed.</span></span> <span data-ttu-id="b7e72-119">Son olarak, `GetReversedStream` giriş alan ve döndüren bir `Stream` (akış).</span><span class="sxs-lookup"><span data-stu-id="b7e72-119">Finally, `GetReversedStream` takes no inputs and returns a `Stream` (streamed).</span></span>  
  
2. <span data-ttu-id="b7e72-120">Akış bağlamadaki etkinleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7e72-120">Streaming must be enabled on the binding.</span></span> <span data-ttu-id="b7e72-121">Ayarladığınız bir `TransferMode` özelliği şu değerlerden birini alabilir:</span><span class="sxs-lookup"><span data-stu-id="b7e72-121">You set a `TransferMode` property, which can take one of the following values:</span></span>  
  
    1. <span data-ttu-id="b7e72-122">`Buffered`,</span><span class="sxs-lookup"><span data-stu-id="b7e72-122">`Buffered`,</span></span>  
  
    2. <span data-ttu-id="b7e72-123">`Streamed`, her iki yönde de akış iletişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b7e72-123">`Streamed`, which enables streaming communication in both directions.</span></span>  
  
    3. <span data-ttu-id="b7e72-124">`StreamedRequest`, yalnızca istek akışı etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="b7e72-124">`StreamedRequest`, which enables streaming the request only.</span></span>  
  
    4. <span data-ttu-id="b7e72-125">`StreamedResponse`, yalnızca yanıt akışı etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="b7e72-125">`StreamedResponse`, which enables streaming the response only.</span></span>  
  
     <span data-ttu-id="b7e72-126">`BasicHttpBinding` Sunan `TransferMode` aynı bağlama özelliğinin `NetTcpBinding` ve `NetNamedPipeBinding`.</span><span class="sxs-lookup"><span data-stu-id="b7e72-126">The `BasicHttpBinding` exposes the `TransferMode` property on the binding, as does `NetTcpBinding` and `NetNamedPipeBinding`.</span></span> <span data-ttu-id="b7e72-127">`TransferMode` Özelliği ayrıca aktarım bağlama öğede ayarlama ve kullanılan özel bir bağlama.</span><span class="sxs-lookup"><span data-stu-id="b7e72-127">The `TransferMode` property can also be set on the transport binding element and used in a custom binding.</span></span>  
  
     <span data-ttu-id="b7e72-128">Aşağıdaki örnekler nasıl belirleyeceğinizi `TransferMode` kod ve yapılandırma dosyasını değiştirerek.</span><span class="sxs-lookup"><span data-stu-id="b7e72-128">The following samples show how to set `TransferMode` by code and by changing the configuration file.</span></span> <span data-ttu-id="b7e72-129">Her ikisi de ayarlanmış örnekleri `maxReceivedMessageSize` yerleştirir iletileri izin verilen en büyük boyutu için üst sınır 64 MB özelliğini alır.</span><span class="sxs-lookup"><span data-stu-id="b7e72-129">The samples also both set the `maxReceivedMessageSize` property to 64 MB, which places a cap on the maximum allowable size of messages on receive.</span></span> <span data-ttu-id="b7e72-130">Varsayılan `maxReceivedMessageSize` genellikle akış senaryoları için düşükse, 64 KB ' tır.</span><span class="sxs-lookup"><span data-stu-id="b7e72-130">The default `maxReceivedMessageSize` is 64 KB, which is usually too low for streaming scenarios.</span></span> <span data-ttu-id="b7e72-131">Bu kota ayarı iletileri almak için uygulamanızı bekliyor en büyük boyutuna bağlı olarak uygun şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b7e72-131">Set this quota setting as appropriate depending on the maximum size of messages your application expects to receive.</span></span> <span data-ttu-id="b7e72-132">Ayrıca `maxBufferSize` arabelleğe alınır ve uygun şekilde ayarlanmış maksimum boyutu denetler.</span><span class="sxs-lookup"><span data-stu-id="b7e72-132">Also note that `maxBufferSize` controls the maximum size that is buffered, and set it appropriately.</span></span>  
  
    1. <span data-ttu-id="b7e72-133">Ayar örneği aşağıdaki yapılandırma parçacığından gösterir `TransferMode` üzerinde akış özelliği `basicHttpBinding` ve özel bir HTTP bağlaması.</span><span class="sxs-lookup"><span data-stu-id="b7e72-133">The following configuration snippet from the sample shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding.</span></span>  
  
         [!code-xml[c_HowTo_EnableStreaming#103](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/common/app.config#103)]   
  
    2. <span data-ttu-id="b7e72-134">Aşağıdaki kod parçacığı ayarını gösterir `TransferMode` üzerinde akış özelliği `basicHttpBinding` ve özel bir HTTP bağlaması.</span><span class="sxs-lookup"><span data-stu-id="b7e72-134">The following code snippet shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding.</span></span>  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#2)]
         [!code-vb[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#2)]  
  
    3. <span data-ttu-id="b7e72-135">Aşağıdaki kod parçacığı ayarını gösterir `TransferMode` özel TCP bağlamada akış özelliği.</span><span class="sxs-lookup"><span data-stu-id="b7e72-135">The following code snippet shows setting the `TransferMode` property to streaming on a custom TCP binding.</span></span>  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#3)]
         [!code-vb[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#3)]  
  
3. <span data-ttu-id="b7e72-136">İşlemleri `GetStream`, `UploadStream`, ve `EchoStream` tüm baş doğrudan bir dosyadan veri gönderen veya alınan verileri bir dosyaya kaydetme.</span><span class="sxs-lookup"><span data-stu-id="b7e72-136">The operations `GetStream`, `UploadStream`, and `EchoStream` all deal with sending data directly from a file or saving received data directly to a file.</span></span> <span data-ttu-id="b7e72-137">Aşağıdaki kod içindir `GetStream`.</span><span class="sxs-lookup"><span data-stu-id="b7e72-137">The following code is for `GetStream`.</span></span>  
  
     [!code-csharp[c_HowTo_EnableStreaming#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#4)]
     [!code-vb[c_HowTo_EnableStreaming#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#4)]  
  
### <a name="writing-a-custom-stream"></a><span data-ttu-id="b7e72-138">Özel bir akış yazma</span><span class="sxs-lookup"><span data-stu-id="b7e72-138">Writing a custom stream</span></span>  
  
1. <span data-ttu-id="b7e72-139">Bunu gönderildiği sırada bir veri akışı, her bir öbeği özel işleme yapmak veya alınan özel akış sınıfından türetilen <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="b7e72-139">To do special processing on each chunk of a data stream as it is being sent or received, derive a custom stream class from <xref:System.IO.Stream>.</span></span> <span data-ttu-id="b7e72-140">Özel bir akışa ilişkin bir örnek olarak, aşağıdaki kodu içeren bir `GetReversedStream` yöntemi ve bir `ReverseStream` sınıfı-.</span><span class="sxs-lookup"><span data-stu-id="b7e72-140">As an example of a custom stream, the following code contains a `GetReversedStream` method and a `ReverseStream` class-.</span></span>  
  
     <span data-ttu-id="b7e72-141">`GetReversedStream` oluşturur ve yeni bir örneğini döndürür `ReverseStream`.</span><span class="sxs-lookup"><span data-stu-id="b7e72-141">`GetReversedStream` creates and returns a new instance of `ReverseStream`.</span></span> <span data-ttu-id="b7e72-142">Sistem okur gibi gerçek işleme olur `ReverseStream` nesne.</span><span class="sxs-lookup"><span data-stu-id="b7e72-142">The actual processing happens as the system reads from the `ReverseStream` object.</span></span> <span data-ttu-id="b7e72-143">`ReverseStream.Read` Yöntemi bayt öbeğini temel alınan dosyadan okur, bunları tersine çevirir ve sonra ters bayt sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="b7e72-143">The `ReverseStream.Read` method reads a chunk of bytes from the underlying file, reverses them, then returns the reversed bytes.</span></span> <span data-ttu-id="b7e72-144">Bu yöntem, tüm dosya içeriğini ters değil; bir kerede bir bayt bir öbek tersine çevirir.</span><span class="sxs-lookup"><span data-stu-id="b7e72-144">This method does not reverse the entire file content; it reverses one chunk of bytes at a time.</span></span> <span data-ttu-id="b7e72-145">Bu örnek, içeriği olarak akış işlemede nasıl gerçekleştirebileceğiniz gösterir akıştan yazılamaz veya okunamaz için okuyun.</span><span class="sxs-lookup"><span data-stu-id="b7e72-145">This example shows how you can perform stream processing as the content is being read to or written from the stream.</span></span>  
  
     [!code-csharp[c_HowTo_EnableStreaming#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#2)]
     [!code-vb[c_HowTo_EnableStreaming#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="b7e72-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7e72-146">See also</span></span>

- [<span data-ttu-id="b7e72-147">Büyük Veriler ve Akış Yapma</span><span class="sxs-lookup"><span data-stu-id="b7e72-147">Large Data and Streaming</span></span>](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)
- [<span data-ttu-id="b7e72-148">Akış</span><span class="sxs-lookup"><span data-stu-id="b7e72-148">Stream</span></span>](../../../../docs/framework/wcf/samples/stream.md)
