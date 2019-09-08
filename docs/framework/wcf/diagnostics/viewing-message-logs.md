---
title: İleti Günlüklerini Görüntüleme
ms.date: 03/30/2017
ms.assetid: 3012fa13-f650-45fb-aaea-c5cca8c7d372
ms.openlocfilehash: b0f35d4cca037e663c5c298103c4a8228bb16d52
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797313"
---
# <a name="viewing-message-logs"></a><span data-ttu-id="3b6fe-102">İleti Günlüklerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="3b6fe-102">Viewing Message Logs</span></span>
<span data-ttu-id="3b6fe-103">Bu konu başlığı altında, ileti günlüklerini nasıl görüntüleyebileceğiniz açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3b6fe-103">This topic describes how you can view message logs.</span></span>  
  
## <a name="viewing-message-logs-in-the-service-trace-viewer"></a><span data-ttu-id="3b6fe-104">Hizmet Izleme görüntüleyicisinde Ileti günlüklerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="3b6fe-104">Viewing Message Logs in the Service Trace Viewer</span></span>  
 <span data-ttu-id="3b6fe-105">WCF tarafından işlendiği için bir ileti dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="3b6fe-105">A message will be transformed as it is processed by WCF.</span></span> <span data-ttu-id="3b6fe-106">Bu nedenle, günlüğe kaydedilen bir ileti, iletideki içeriği değil, yalnızca iletinin günlüğe kaydedildiği noktada yansıtır.</span><span class="sxs-lookup"><span data-stu-id="3b6fe-106">Therefore, a message being logged reflects only the message's content at the point it was logged, not the content on the wire.</span></span>  
  
 <span data-ttu-id="3b6fe-107">İleti günlüğe kaydetme çıkışında iletinin aktarım biçimiyle hiçbir ilişki bulunmadığından, ileti günlüğü her zaman kodu çözülen iletiyi verir.</span><span class="sxs-lookup"><span data-stu-id="3b6fe-107">Since the output of message logging has no relationship to the transfer format of the message, message logging always outputs the decoded message.</span></span> <span data-ttu-id="3b6fe-108">İleti günlüğe kaydetmeyi doğru şekilde yapılandırdıysanız, günlüğe kaydedilen tüm iletiler düz metin biçiminde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3b6fe-108">If you have configured message logging properly, any logged message should be in plain text.</span></span> <span data-ttu-id="3b6fe-109">Örneğin, günlüğe kaydedilen iletilerin biçimi (düz metin) bir ikili ileti Kodlayıcısı kullanımından etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="3b6fe-109">For example, the format (plain text) of the logged messages is not affected by the usage of a binary message encoder.</span></span>  
  
 <span data-ttu-id="3b6fe-110">XmlWriterTraceListener çıkışı, XML parçaları dizisi içeren bir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="3b6fe-110">The output of the XmlWriterTraceListener is a file that contains a sequence of XML fragments.</span></span> <span data-ttu-id="3b6fe-111">Dosyanın geçerli bir XML dosyası olmadığı farkında olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="3b6fe-111">You should be aware that the file is not a valid XML file.</span></span> <span data-ttu-id="3b6fe-112">İleti günlüğü dosyalarını görüntülemek için [hizmet Izleme Görüntüleyicisi aracı 'nı (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) kullanmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="3b6fe-112">It is recommended that you use the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) to view the message log files.</span></span> <span data-ttu-id="3b6fe-113">Bu aracın nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [Ilişkili izlemeleri ve sorun gidermeyi görüntülemek Için hizmet Izleme görüntüleyicisini kullanma](./tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="3b6fe-113">For more information on how to use this tool, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](./tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="3b6fe-114">Hizmet Izleme görüntüleyicisinde iletiler **ileti** sekmesinde listelenir. Oluşan veya ilişkili olan iletiler, hatanın önem derecesine bağlı olarak bir işleme hatası sarı (uyarı düzeyi) veya kırmızı (hata düzeyi) olarak vurgulanır.</span><span class="sxs-lookup"><span data-stu-id="3b6fe-114">In the Service Trace Viewer, messages are listed in the **Message** tab. Messages that have caused, or are related to, a processing error are highlighted in yellow (warning level) or red (error level), depending on the severity of the error.</span></span> <span data-ttu-id="3b6fe-115">İletiye çift tıklamak, işleme isteği bağlamında ileti izlemeyi getirir.</span><span class="sxs-lookup"><span data-stu-id="3b6fe-115">Double-clicking on the message brings up the message trace in the context of the processing request.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3b6fe-116">Bir iletinin üstbilgisi yoksa, hiçbir `<header/>` etiket kaydedilmez.</span><span class="sxs-lookup"><span data-stu-id="3b6fe-116">If a message has no header, no `<header/>` tag is logged.</span></span>  
  
## <a name="viewing-messages-logged-by-a-client-a-relay-and-a-service"></a><span data-ttu-id="3b6fe-117">Istemci, geçiş ve hizmet tarafından günlüğe kaydedilen Iletileri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="3b6fe-117">Viewing Messages Logged by a Client, a Relay, and a Service</span></span>  
 <span data-ttu-id="3b6fe-118">Ortamınız, daha sonra iletiyi hizmete ileten bir geçişe ileti gönderen bir istemci içeriyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="3b6fe-118">Your environment may contain a client, which sends a message to a relay, that subsequently forwards the message to the service.</span></span> <span data-ttu-id="3b6fe-119">Her üç konumda ileti günlüğe kaydetme etkin olduğunda ve üç ileti günlüğü de [hizmet Izleme Görüntüleyicisi Aracı (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) içinde aynı anda görüntülendiğinde, ileti günlüğü alışverişleri yanlış işlenir.</span><span class="sxs-lookup"><span data-stu-id="3b6fe-119">When message logging is enabled on all three locations, and all three message logs are viewed in [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) simultaneously, the message log exchanges will be incorrectly rendered.</span></span> <span data-ttu-id="3b6fe-120">Bunun nedeni, ileti `CorrelationId` üstbilgisindeki `ActivityId` ve içindeki her gönderme alma çiftinin benzersiz olmaması nedeniyle oluşur.</span><span class="sxs-lookup"><span data-stu-id="3b6fe-120">This is because the `CorrelationId` and `ActivityId` in the Message header are not unique for every send-receive pair.</span></span>  
  
 <span data-ttu-id="3b6fe-121">Bu sorunu çözmek için aşağıdaki yöntemlerden birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b6fe-121">You can use either one of the following methods to resolve this problem.</span></span>  
  
- <span data-ttu-id="3b6fe-122">[Hizmet Izleme Görüntüleyicisi Aracı (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) içindeki üç ileti günlüğünün ikisini de her zaman görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="3b6fe-122">Only view two of the three message logs in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) at any time.</span></span>  
  
- <span data-ttu-id="3b6fe-123">[Hizmet izleme Görüntüleyicisi aracında (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) tüm üç günlüğü aynı anda görüntülemeniz gerekiyorsa, yeni <xref:System.ServiceModel.Channels.Message> bir örnek oluşturarak geçiş hizmetini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b6fe-123">If you must view all three logs in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) at the same time, you can modify the relay service by creating a new <xref:System.ServiceModel.Channels.Message> instance.</span></span> <span data-ttu-id="3b6fe-124">Bu örnek, gelen ileti gövdesinin bir kopyası olmalıdır `ActivityId` ve ve `Action` üst bilgileri hariç tüm üst bilgileri içermelidir.</span><span class="sxs-lookup"><span data-stu-id="3b6fe-124">This instance should be a copy of the body of the incoming message, plus all the headers except for the `ActivityId` and `Action` headers.</span></span> <span data-ttu-id="3b6fe-125">Aşağıdaki örnek kodda bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3b6fe-125">The following example code demonstrates how to do this.</span></span>  
  
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
  
## <a name="exceptional-cases-for-inaccurate-message-logging-content"></a><span data-ttu-id="3b6fe-126">Hatalı Ileti günlüğü Içeriği için olağanüstü durumlar</span><span class="sxs-lookup"><span data-stu-id="3b6fe-126">Exceptional Cases for Inaccurate Message Logging Content</span></span>  
 <span data-ttu-id="3b6fe-127">Aşağıdaki koşullarda günlüğe yazılan iletiler, tel üzerinde mevcut olan sekizli akışın tam temsili olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="3b6fe-127">Under the following conditions, messages being logged might not be the exact representation of the octet stream present on the wire.</span></span>  
  
- <span data-ttu-id="3b6fe-128">BasicHttpBinding için,/Addressing/None ad alanındaki gelen iletiler için zarf üstbilgileri günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="3b6fe-128">For BasicHttpBinding, envelope headers are logged for the incoming messages in the /addressing/none namespace.</span></span>  
  
- <span data-ttu-id="3b6fe-129">Boşluk, uyumsuz olabilir.</span><span class="sxs-lookup"><span data-stu-id="3b6fe-129">White spaces can be mismatched.</span></span>  
  
- <span data-ttu-id="3b6fe-130">Gelen iletilerde boş öğeler farklı gösterilebilir.</span><span class="sxs-lookup"><span data-stu-id="3b6fe-130">For incoming messages, empty elements can be represented differently.</span></span> <span data-ttu-id="3b6fe-131">Örneğin, \<etiket/>\<yerine \<etiket >/Tag ></span><span class="sxs-lookup"><span data-stu-id="3b6fe-131">For example, \<tag>\</tag> instead of  \<tag/></span></span>  
  
- <span data-ttu-id="3b6fe-132">Bilinen PII günlüğü varsayılan olarak devre dışı bırakıldığında ya da enableLoggingKnownPII = "true" ayarını Açık olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3b6fe-132">When known PII logging is disabled either by default or explicit setting enableLoggingKnownPii="true".</span></span>  
  
- <span data-ttu-id="3b6fe-133">Kodlama UTF-8 ' e dönüştürmek için etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3b6fe-133">Encoding is enabled for transforming to UTF-8.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b6fe-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b6fe-134">See also</span></span>

- [<span data-ttu-id="3b6fe-135">Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="3b6fe-135">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../service-trace-viewer-tool-svctraceviewer-exe.md)
- [<span data-ttu-id="3b6fe-136">İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma</span><span class="sxs-lookup"><span data-stu-id="3b6fe-136">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](./tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="3b6fe-137">Günlüğe İleti Kaydetme</span><span class="sxs-lookup"><span data-stu-id="3b6fe-137">Message Logging</span></span>](message-logging.md)
