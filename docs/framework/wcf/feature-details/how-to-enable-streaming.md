---
title: 'Nasıl yapılır: Akışı Etkinleştirme'
description: İşlem yapılmadan önce tamamen alınması gereken varsayılan arabelleğe alınmış aktarımlar yerine WCF 'de akış iletileri etkinleştirmeyi öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6ca2cf4b-c7a1-49d8-a79b-843a90556ba4
ms.openlocfilehash: 538fd8634094aa6fbf097ddb94469d7bca749a63
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247032"
---
# <a name="how-to-enable-streaming"></a><span data-ttu-id="16cfe-103">Nasıl yapılır: Akışı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="16cfe-103">How to: Enable Streaming</span></span>
<span data-ttu-id="16cfe-104">Windows Communication Foundation (WCF), arabelleğe alınmış veya akış aktarımları kullanarak ileti gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="16cfe-104">Windows Communication Foundation (WCF) can send messages using either buffered or streamed transfers.</span></span> <span data-ttu-id="16cfe-105">Varsayılan arabelleğe alınmış Aktarım modunda, bir alıcının okuyabilmesi için bir iletinin tamamen teslim edilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="16cfe-105">In the default buffered-transfer mode, a message must be completely delivered before a receiver can read it.</span></span> <span data-ttu-id="16cfe-106">Akış Aktarım modunda, alıcı tamamen teslim edilmeden önce iletiyi işlemeye başlayabilir.</span><span class="sxs-lookup"><span data-stu-id="16cfe-106">In streaming transfer mode, the receiver can begin to process the message before it is completely delivered.</span></span> <span data-ttu-id="16cfe-107">Aktarım modu, iletilen bilgiler uzun olduğunda ve hizmet dışı olarak işlenebilmesi durumunda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="16cfe-107">The streaming mode is useful when the information that is passed is lengthy and can be processed serially.</span></span> <span data-ttu-id="16cfe-108">İleti tamamen arabelleğe alınamayacak kadar büyük olduğunda akış modu da yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="16cfe-108">Streaming mode is also useful when the message is too large to be entirely buffered.</span></span>  
  
 <span data-ttu-id="16cfe-109">Akışı etkinleştirmek için, `OperationContract` Aktarım düzeyinde uygun bir şekilde tanımlayın ve akışı etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="16cfe-109">To enable streaming, define the `OperationContract` appropriately and enable streaming at the transport level.</span></span>  
  
### <a name="to-stream-data"></a><span data-ttu-id="16cfe-110">Veri akışı için</span><span class="sxs-lookup"><span data-stu-id="16cfe-110">To stream data</span></span>  
  
1. <span data-ttu-id="16cfe-111">Veri akışı için, `OperationContract` hizmetin iki gereksinimi karşılaması gerekir:</span><span class="sxs-lookup"><span data-stu-id="16cfe-111">To stream data, the `OperationContract` for the service must satisfy two requirements:</span></span>  
  
    1. <span data-ttu-id="16cfe-112">Akışa eklenecek verileri tutan parametrenin yöntemdeki tek parametre olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="16cfe-112">The parameter that holds the data to be streamed must be the only parameter in the method.</span></span> <span data-ttu-id="16cfe-113">Örneğin, giriş iletisi akışla bir giriş ise, işlemin tam olarak bir giriş parametresi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="16cfe-113">For example, if the input message is the one to be streamed, the operation must have exactly one input parameter.</span></span> <span data-ttu-id="16cfe-114">Benzer şekilde, çıkış iletisi akışı ise, işlemin tam olarak bir çıkış parametresi veya dönüş değeri olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="16cfe-114">Similarly, if the output message is to be streamed, the operation must have either exactly one output parameter or a return value.</span></span>  
  
    2. <span data-ttu-id="16cfe-115">Parametre ve dönüş değerinin en az biri, ya da olmalıdır <xref:System.IO.Stream> <xref:System.ServiceModel.Channels.Message> <xref:System.Xml.Serialization.IXmlSerializable> .</span><span class="sxs-lookup"><span data-stu-id="16cfe-115">At least one of the types of the parameter and return value must be either <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, or <xref:System.Xml.Serialization.IXmlSerializable>.</span></span>  
  
     <span data-ttu-id="16cfe-116">Aşağıda akış verileri için bir sözleşme örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="16cfe-116">The following is an example of a contract for streamed data.</span></span>  
  
     [!code-csharp[c_HowTo_EnableStreaming#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#1)]
     [!code-vb[c_HowTo_EnableStreaming#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#1)]  
  
     <span data-ttu-id="16cfe-117">İşlem, ara belleğe `GetStream` alınmış bir olarak bazı arabellekli giriş verileri alır `string` ve akış olan bir döndürür `Stream` .</span><span class="sxs-lookup"><span data-stu-id="16cfe-117">The `GetStream` operation receives some buffered input data as a `string`, which is buffered, and returns a `Stream`, which is streamed.</span></span> <span data-ttu-id="16cfe-118">Bunun tersine `UploadStream` bir `Stream` (akışlı) alır ve `bool` (ara belleğe alınmış) döndürür.</span><span class="sxs-lookup"><span data-stu-id="16cfe-118">Conversely `UploadStream` takes in a `Stream` (streamed) and returns a `bool` (buffered).</span></span> <span data-ttu-id="16cfe-119">`EchoStream`, `Stream` giriş ve çıkış iletilerinin her ikisi de akışındaki bir işlemin örneğini alır ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="16cfe-119">`EchoStream` takes and returns `Stream` and is an example of an operation whose input and output messages are both streamed.</span></span> <span data-ttu-id="16cfe-120">Son olarak, `GetReversedStream` giriş yapılmaz ve `Stream` (akış) döndürür.</span><span class="sxs-lookup"><span data-stu-id="16cfe-120">Finally, `GetReversedStream` takes no inputs and returns a `Stream` (streamed).</span></span>  
  
2. <span data-ttu-id="16cfe-121">Bağlamada akış etkinleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="16cfe-121">Streaming must be enabled on the binding.</span></span> <span data-ttu-id="16cfe-122">`TransferMode`Aşağıdaki değerlerden birini içerebilen bir özellik ayarlarsınız:</span><span class="sxs-lookup"><span data-stu-id="16cfe-122">You set a `TransferMode` property, which can take one of the following values:</span></span>  
  
    1. <span data-ttu-id="16cfe-123">`Buffered`,</span><span class="sxs-lookup"><span data-stu-id="16cfe-123">`Buffered`,</span></span>  
  
    2. <span data-ttu-id="16cfe-124">`Streamed`Her iki yönde de akış iletişimi sağlayan.</span><span class="sxs-lookup"><span data-stu-id="16cfe-124">`Streamed`, which enables streaming communication in both directions.</span></span>  
  
    3. <span data-ttu-id="16cfe-125">`StreamedRequest`, yalnızca isteği akışa izin veren.</span><span class="sxs-lookup"><span data-stu-id="16cfe-125">`StreamedRequest`, which enables streaming the request only.</span></span>  
  
    4. <span data-ttu-id="16cfe-126">`StreamedResponse`yalnızca yanıtı akışa izin veren.</span><span class="sxs-lookup"><span data-stu-id="16cfe-126">`StreamedResponse`, which enables streaming the response only.</span></span>  
  
     <span data-ttu-id="16cfe-127">,, `BasicHttpBinding` `TransferMode` Ve gibi bağlama üzerinde özelliğini kullanıma sunar `NetTcpBinding` `NetNamedPipeBinding` .</span><span class="sxs-lookup"><span data-stu-id="16cfe-127">The `BasicHttpBinding` exposes the `TransferMode` property on the binding, as does `NetTcpBinding` and `NetNamedPipeBinding`.</span></span> <span data-ttu-id="16cfe-128">`TransferMode`Özelliği, aktarım bağlama öğesinde de ayarlanabilir ve özel bir bağlamada kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="16cfe-128">The `TransferMode` property can also be set on the transport binding element and used in a custom binding.</span></span>  
  
     <span data-ttu-id="16cfe-129">Aşağıdaki örnekler, `TransferMode` kod ile ve yapılandırma dosyasını değiştirerek nasıl ayarlanacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="16cfe-129">The following samples show how to set `TransferMode` by code and by changing the configuration file.</span></span> <span data-ttu-id="16cfe-130">Ayrıca örneklerin her ikisi de `maxReceivedMessageSize` , alma sırasında izin verilen en fazla ileti boyutuna bir sınır yerleştiren, özelliği 64 MB olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="16cfe-130">The samples also both set the `maxReceivedMessageSize` property to 64 MB, which places a cap on the maximum allowable size of messages on receive.</span></span> <span data-ttu-id="16cfe-131">Varsayılan değer, `maxReceivedMessageSize` genellikle akış senaryolarında çok düşük olan 64 KB 'tır.</span><span class="sxs-lookup"><span data-stu-id="16cfe-131">The default `maxReceivedMessageSize` is 64 KB, which is usually too low for streaming scenarios.</span></span> <span data-ttu-id="16cfe-132">Uygulamanızın almasını beklediği en fazla ileti boyutuna bağlı olarak bu kota ayarını uygun şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="16cfe-132">Set this quota setting as appropriate depending on the maximum size of messages your application expects to receive.</span></span> <span data-ttu-id="16cfe-133">Ayrıca `maxBufferSize` , arabelleğe alınan en büyük boyutu denetler ve uygun şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="16cfe-133">Also note that `maxBufferSize` controls the maximum size that is buffered, and set it appropriately.</span></span>  
  
    1. <span data-ttu-id="16cfe-134">Örnekteki aşağıdaki yapılandırma kod parçacığı, `TransferMode` özelliğinin `basicHttpBinding` ve özel bir http bağlamasındaki akış için ayarlanmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="16cfe-134">The following configuration snippet from the sample shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding.</span></span>  
  
         [!code-xml[c_HowTo_EnableStreaming#103](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/common/app.config#103)]
  
    2. <span data-ttu-id="16cfe-135">Aşağıdaki kod parçacığı, `TransferMode` `basicHttpBinding` ve özel bir http bağlamasındaki özelliği akışa alma özelliğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="16cfe-135">The following code snippet shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding.</span></span>  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#2)]
         [!code-vb[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#2)]  
  
    3. <span data-ttu-id="16cfe-136">Aşağıdaki kod parçacığı, `TransferMode` özelliği özel bır TCP bağlamasındaki akışa ayarlamayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="16cfe-136">The following code snippet shows setting the `TransferMode` property to streaming on a custom TCP binding.</span></span>  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#3)]
         [!code-vb[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#3)]  
  
3. <span data-ttu-id="16cfe-137">İşlemler `GetStream` , `UploadStream` ve `EchoStream` hepsi doğrudan bir dosyadan veri göndermeye veya alınan verileri doğrudan bir dosyaya kaydetmeye yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="16cfe-137">The operations `GetStream`, `UploadStream`, and `EchoStream` all deal with sending data directly from a file or saving received data directly to a file.</span></span> <span data-ttu-id="16cfe-138">Aşağıdaki kod içindir `GetStream` .</span><span class="sxs-lookup"><span data-stu-id="16cfe-138">The following code is for `GetStream`.</span></span>  
  
     [!code-csharp[c_HowTo_EnableStreaming#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#4)]
     [!code-vb[c_HowTo_EnableStreaming#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#4)]  
  
### <a name="writing-a-custom-stream"></a><span data-ttu-id="16cfe-139">Özel akış yazma</span><span class="sxs-lookup"><span data-stu-id="16cfe-139">Writing a custom stream</span></span>  
  
1. <span data-ttu-id="16cfe-140">Gönderilen veya alınan bir veri akışının her öbeğiyle özel işlem yapmak için, öğesinden özel bir akış sınıfı türetirsiniz <xref:System.IO.Stream> .</span><span class="sxs-lookup"><span data-stu-id="16cfe-140">To do special processing on each chunk of a data stream as it is being sent or received, derive a custom stream class from <xref:System.IO.Stream>.</span></span> <span data-ttu-id="16cfe-141">Özel bir akışa örnek olarak aşağıdaki kod bir `GetReversedStream` yöntemi ve bir `ReverseStream` sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="16cfe-141">As an example of a custom stream, the following code contains a `GetReversedStream` method and a `ReverseStream` class-.</span></span>  
  
     <span data-ttu-id="16cfe-142">`GetReversedStream`Yeni bir örneğini oluşturur ve döndürür `ReverseStream` .</span><span class="sxs-lookup"><span data-stu-id="16cfe-142">`GetReversedStream` creates and returns a new instance of `ReverseStream`.</span></span> <span data-ttu-id="16cfe-143">Gerçek işlem, nesneden sistem okuduğunda oluşur `ReverseStream` .</span><span class="sxs-lookup"><span data-stu-id="16cfe-143">The actual processing happens as the system reads from the `ReverseStream` object.</span></span> <span data-ttu-id="16cfe-144">`ReverseStream.Read`Yöntemi, temel alınan dosyadaki bir bayt öbeğini okur, bunları tersine çevirir ve ters bayt döndürür.</span><span class="sxs-lookup"><span data-stu-id="16cfe-144">The `ReverseStream.Read` method reads a chunk of bytes from the underlying file, reverses them, then returns the reversed bytes.</span></span> <span data-ttu-id="16cfe-145">Bu yöntem, tüm dosya içeriğini tersine almaz; tek seferde bir bayt öbeğini tersine çevirir.</span><span class="sxs-lookup"><span data-stu-id="16cfe-145">This method does not reverse the entire file content; it reverses one chunk of bytes at a time.</span></span> <span data-ttu-id="16cfe-146">Bu örnek, içerik okuma veya akışa yazma sırasında akış işlemeyi nasıl gerçekleştirebileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="16cfe-146">This example shows how you can perform stream processing as the content is being read to or written from the stream.</span></span>  
  
     [!code-csharp[c_HowTo_EnableStreaming#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#2)]
     [!code-vb[c_HowTo_EnableStreaming#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="16cfe-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16cfe-147">See also</span></span>

- [<span data-ttu-id="16cfe-148">Büyük Veriler ve Akış Yapma</span><span class="sxs-lookup"><span data-stu-id="16cfe-148">Large Data and Streaming</span></span>](large-data-and-streaming.md)
- [<span data-ttu-id="16cfe-149">Akış</span><span class="sxs-lookup"><span data-stu-id="16cfe-149">Stream</span></span>](../samples/stream.md)
