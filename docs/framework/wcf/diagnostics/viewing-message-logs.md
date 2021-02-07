---
description: 'Hakkında daha fazla bilgi edinin: Ileti günlüklerini görüntüleme'
title: İleti Günlüklerini Görüntüleme
ms.date: 03/30/2017
ms.assetid: 3012fa13-f650-45fb-aaea-c5cca8c7d372
ms.openlocfilehash: c640b2c3793839be4a31123701865fa944eaebc8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99758040"
---
# <a name="viewing-message-logs"></a><span data-ttu-id="a0c60-103">İleti Günlüklerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="a0c60-103">Viewing Message Logs</span></span>

<span data-ttu-id="a0c60-104">Bu konu başlığı altında, ileti günlüklerini nasıl görüntüleyebileceğiniz açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a0c60-104">This topic describes how you can view message logs.</span></span>  
  
## <a name="viewing-message-logs-in-the-service-trace-viewer"></a><span data-ttu-id="a0c60-105">Hizmet Izleme görüntüleyicisinde Ileti günlüklerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="a0c60-105">Viewing Message Logs in the Service Trace Viewer</span></span>  

 <span data-ttu-id="a0c60-106">WCF tarafından işlendiği için bir ileti dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="a0c60-106">A message will be transformed as it is processed by WCF.</span></span> <span data-ttu-id="a0c60-107">Bu nedenle, günlüğe kaydedilen bir ileti, iletideki içeriği değil, yalnızca iletinin günlüğe kaydedildiği noktada yansıtır.</span><span class="sxs-lookup"><span data-stu-id="a0c60-107">Therefore, a message being logged reflects only the message's content at the point it was logged, not the content on the wire.</span></span>  
  
 <span data-ttu-id="a0c60-108">İleti günlüğe kaydetme çıkışında iletinin aktarım biçimiyle hiçbir ilişki bulunmadığından, ileti günlüğü her zaman kodu çözülen iletiyi verir.</span><span class="sxs-lookup"><span data-stu-id="a0c60-108">Since the output of message logging has no relationship to the transfer format of the message, message logging always outputs the decoded message.</span></span> <span data-ttu-id="a0c60-109">İleti günlüğe kaydetmeyi doğru şekilde yapılandırdıysanız, günlüğe kaydedilen tüm iletiler düz metin biçiminde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a0c60-109">If you have configured message logging properly, any logged message should be in plain text.</span></span> <span data-ttu-id="a0c60-110">Örneğin, günlüğe kaydedilen iletilerin biçimi (düz metin) bir ikili ileti Kodlayıcısı kullanımından etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="a0c60-110">For example, the format (plain text) of the logged messages is not affected by the usage of a binary message encoder.</span></span>  
  
 <span data-ttu-id="a0c60-111">XmlWriterTraceListener çıkışı, XML parçaları dizisi içeren bir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="a0c60-111">The output of the XmlWriterTraceListener is a file that contains a sequence of XML fragments.</span></span> <span data-ttu-id="a0c60-112">Dosyanın geçerli bir XML dosyası olmadığı farkında olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="a0c60-112">You should be aware that the file is not a valid XML file.</span></span> <span data-ttu-id="a0c60-113">İleti günlüğü dosyalarını görüntülemek için [hizmet Izleme Görüntüleyicisi aracı 'nı (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) kullanmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="a0c60-113">It is recommended that you use the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) to view the message log files.</span></span> <span data-ttu-id="a0c60-114">Bu aracın nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [Ilişkili izlemeleri ve sorun gidermeyi görüntülemek Için hizmet Izleme görüntüleyicisini kullanma](./tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="a0c60-114">For more information on how to use this tool, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](./tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="a0c60-115">Hizmet Izleme görüntüleyicisinde iletiler **ileti** sekmesinde listelenir. Oluşan veya ilişkili olan iletiler, hatanın önem derecesine bağlı olarak bir işleme hatası sarı (uyarı düzeyi) veya kırmızı (hata düzeyi) olarak vurgulanır.</span><span class="sxs-lookup"><span data-stu-id="a0c60-115">In the Service Trace Viewer, messages are listed in the **Message** tab. Messages that have caused, or are related to, a processing error are highlighted in yellow (warning level) or red (error level), depending on the severity of the error.</span></span> <span data-ttu-id="a0c60-116">İletiye çift tıklamak, işleme isteği bağlamında ileti izlemeyi getirir.</span><span class="sxs-lookup"><span data-stu-id="a0c60-116">Double-clicking on the message brings up the message trace in the context of the processing request.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a0c60-117">Bir iletinin üstbilgisi yoksa, hiçbir `<header/>` etiket kaydedilmez.</span><span class="sxs-lookup"><span data-stu-id="a0c60-117">If a message has no header, no `<header/>` tag is logged.</span></span>  
  
## <a name="viewing-messages-logged-by-a-client-a-relay-and-a-service"></a><span data-ttu-id="a0c60-118">Istemci, geçiş ve hizmet tarafından günlüğe kaydedilen Iletileri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="a0c60-118">Viewing Messages Logged by a Client, a Relay, and a Service</span></span>  

 <span data-ttu-id="a0c60-119">Ortamınız, daha sonra iletiyi hizmete ileten bir geçişe ileti gönderen bir istemci içeriyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="a0c60-119">Your environment may contain a client, which sends a message to a relay, that subsequently forwards the message to the service.</span></span> <span data-ttu-id="a0c60-120">Her üç konumda ileti günlüğe kaydetme etkin olduğunda ve üç ileti günlüğü de aynı anda [Service Trace Görüntüleyici aracında (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) görüntüleniyorsa ileti günlüğü alışverişleri yanlış işlenir.</span><span class="sxs-lookup"><span data-stu-id="a0c60-120">When message logging is enabled on all three locations, and all three message logs are viewed in [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) simultaneously, the message log exchanges will be incorrectly rendered.</span></span> <span data-ttu-id="a0c60-121">Bunun nedeni, `CorrelationId` `ActivityId` ileti üstbilgisindeki ve içindeki her gönderme alma çiftinin benzersiz olmaması nedeniyle oluşur.</span><span class="sxs-lookup"><span data-stu-id="a0c60-121">This is because the `CorrelationId` and `ActivityId` in the Message header are not unique for every send-receive pair.</span></span>  
  
 <span data-ttu-id="a0c60-122">Bu sorunu çözmek için aşağıdaki yöntemlerden birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0c60-122">You can use either one of the following methods to resolve this problem.</span></span>  
  
- <span data-ttu-id="a0c60-123">[Hizmet Izleme Görüntüleyicisi aracında (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) her zaman yalnızca üç ileti günlüğünün ikisini görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="a0c60-123">Only view two of the three message logs in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) at any time.</span></span>  
  
- <span data-ttu-id="a0c60-124">[Service Trace Viewer aracında (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) tüm üç günlüğü aynı anda görüntülemeniz gerekiyorsa, yeni bir örnek oluşturarak geçiş hizmetini değiştirebilirsiniz <xref:System.ServiceModel.Channels.Message> .</span><span class="sxs-lookup"><span data-stu-id="a0c60-124">If you must view all three logs in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) at the same time, you can modify the relay service by creating a new <xref:System.ServiceModel.Channels.Message> instance.</span></span> <span data-ttu-id="a0c60-125">Bu örnek, gelen ileti gövdesinin bir kopyası olmalıdır `ActivityId` ve ve üst bilgileri hariç tüm üst bilgileri içermelidir `Action` .</span><span class="sxs-lookup"><span data-stu-id="a0c60-125">This instance should be a copy of the body of the incoming message, plus all the headers except for the `ActivityId` and `Action` headers.</span></span> <span data-ttu-id="a0c60-126">Aşağıdaki örnek kodda bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a0c60-126">The following example code demonstrates how to do this.</span></span>  
  
```csharp
Message outgoingMessage = Message.CreateMessage(incomingMessage.Version, incomingMessage.Headers.Action, incomingMessage.GetReaderAtBodyContents());  
  
for (int i = 0; i < incomingMessage.Headers.Count; i++)  
{  
   if (incomingMessage.Headers[i].Name.Equals("ActivityId", StringComparison.InvariantCultureIgnoreCase) ||  
incomingMessage.Headers[i].Name.Equals("Action", StringComparison.InvariantCultureIgnoreCase))  
   {  
      continue;  
    }  
    outgoingMessage.Headers.CopyHeaderFrom(incomingMessage, i);  
}  
```  
  
## <a name="exceptional-cases-for-inaccurate-message-logging-content"></a><span data-ttu-id="a0c60-127">Hatalı Ileti günlüğü Içeriği için olağanüstü durumlar</span><span class="sxs-lookup"><span data-stu-id="a0c60-127">Exceptional Cases for Inaccurate Message Logging Content</span></span>  

 <span data-ttu-id="a0c60-128">Aşağıdaki koşullarda günlüğe yazılan iletiler, tel üzerinde mevcut olan sekizli akışın tam temsili olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="a0c60-128">Under the following conditions, messages being logged might not be the exact representation of the octet stream present on the wire.</span></span>  
  
- <span data-ttu-id="a0c60-129">BasicHttpBinding için,/Addressing/None ad alanındaki gelen iletiler için zarf üstbilgileri günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="a0c60-129">For BasicHttpBinding, envelope headers are logged for the incoming messages in the /addressing/none namespace.</span></span>  
  
- <span data-ttu-id="a0c60-130">Boşluk, uyumsuz olabilir.</span><span class="sxs-lookup"><span data-stu-id="a0c60-130">White spaces can be mismatched.</span></span>  
  
- <span data-ttu-id="a0c60-131">Gelen iletilerde boş öğeler farklı gösterilebilir.</span><span class="sxs-lookup"><span data-stu-id="a0c60-131">For incoming messages, empty elements can be represented differently.</span></span> <span data-ttu-id="a0c60-132">Örneğin, \<tag> \</tag> yerine\<tag/></span><span class="sxs-lookup"><span data-stu-id="a0c60-132">For example, \<tag>\</tag> instead of  \<tag/></span></span>  
  
- <span data-ttu-id="a0c60-133">Bilinen PII günlüğü varsayılan olarak devre dışı bırakıldığında ya da enableLoggingKnownPII = "true" ayarını Açık olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a0c60-133">When known PII logging is disabled either by default or explicit setting enableLoggingKnownPii="true".</span></span>  
  
- <span data-ttu-id="a0c60-134">Kodlama UTF-8 ' e dönüştürmek için etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a0c60-134">Encoding is enabled for transforming to UTF-8.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0c60-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0c60-135">See also</span></span>

- [<span data-ttu-id="a0c60-136">Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="a0c60-136">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../service-trace-viewer-tool-svctraceviewer-exe.md)
- [<span data-ttu-id="a0c60-137">İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma</span><span class="sxs-lookup"><span data-stu-id="a0c60-137">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](./tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="a0c60-138">İleti Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="a0c60-138">Message Logging</span></span>](message-logging.md)
