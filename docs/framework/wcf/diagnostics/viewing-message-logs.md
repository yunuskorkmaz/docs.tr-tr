---
title: İleti Günlüklerini Görüntüleme
ms.date: 03/30/2017
ms.assetid: 3012fa13-f650-45fb-aaea-c5cca8c7d372
ms.openlocfilehash: 025d4020002a56deb9d5b8a2fe628f50cabad4d3
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2018
ms.locfileid: "42912094"
---
# <a name="viewing-message-logs"></a><span data-ttu-id="7bb45-102">İleti Günlüklerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="7bb45-102">Viewing Message Logs</span></span>
<span data-ttu-id="7bb45-103">Bu konu, ileti günlüklerini görüntüleme biçimini açıklar.</span><span class="sxs-lookup"><span data-stu-id="7bb45-103">This topic describes how you can view message logs.</span></span>  
  
## <a name="viewing-message-logs-in-the-service-trace-viewer"></a><span data-ttu-id="7bb45-104">İleti görüntüleme hizmet izleme Görüntüleyicisi'nde günlüğe kaydeder</span><span class="sxs-lookup"><span data-stu-id="7bb45-104">Viewing Message Logs in the Service Trace Viewer</span></span>  
 <span data-ttu-id="7bb45-105">WCF tarafından işlendiği bir ileti dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="7bb45-105">A message will be transformed as it is processed by WCF.</span></span> <span data-ttu-id="7bb45-106">Bu nedenle, bir ileti günlüğe kaydedildi. yalnızca ileti içeriği, günlüğe kaydedilen noktasına değil Tel üzerinde içerik yansıtır.</span><span class="sxs-lookup"><span data-stu-id="7bb45-106">Therefore, a message being logged reflects only the message's content at the point it was logged, not the content on the wire.</span></span>  
  
 <span data-ttu-id="7bb45-107">Günlüğe ileti kaydetme çıktısını iletisinin aktarımı biçimi hiçbir ilişkisi olduğundan, her zaman ileti günlüğe kaydetme kodu çözülen ileti çıkarır.</span><span class="sxs-lookup"><span data-stu-id="7bb45-107">Since the output of message logging has no relationship to the transfer format of the message, message logging always outputs the decoded message.</span></span> <span data-ttu-id="7bb45-108">İletileri günlüğe düzgün şekilde yapılandırdıysanız, günlüğe kaydedilen iletiler düz metin biçiminde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7bb45-108">If you have configured message logging properly, any logged message should be in plain text.</span></span> <span data-ttu-id="7bb45-109">Örneğin, günlüğe kaydedilen iletilere biçimi (düz metin), ikili ileti Kodlayıcısı'nın kullanımı etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="7bb45-109">For example, the format (plain text) of the logged messages is not affected by the usage of a binary message encoder.</span></span>  
  
 <span data-ttu-id="7bb45-110">XmlWriterTraceListener çıktısını bir dizi parçalarını içeren bir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="7bb45-110">The output of the XmlWriterTraceListener is a file that contains a sequence of XML fragments.</span></span> <span data-ttu-id="7bb45-111">Dosya geçerli bir XML dosyası değil bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7bb45-111">You should be aware that the file is not a valid XML file.</span></span> <span data-ttu-id="7bb45-112">Kullanmanız önerilir [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) ileti günlük dosyalarını görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="7bb45-112">It is recommended that you use the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) to view the message log files.</span></span> <span data-ttu-id="7bb45-113">Bu aracı kullanma hakkında daha fazla bilgi için bkz. [ilişkilendirilmiş izlemeleri görüntülemek ve sorun giderme için hizmet izleme görüntüleyicisini kullanarak](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="7bb45-113">For more information on how to use this tool, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="7bb45-114">Hizmet izleme Görüntüleyicisi'nde iletileri içinde listelenen **ileti** sekmesi. Neden veya olmayan iletilerini ilgili işleme hatası (uyarı düzeyi), sarı veya kırmızı (hata düzeyi), hatanın önem derecesine bağlı olarak vurgulanır.</span><span class="sxs-lookup"><span data-stu-id="7bb45-114">In the Service Trace Viewer, messages are listed in the **Message** tab. Messages that have caused, or are related to, a processing error are highlighted in yellow (warning level) or red (error level), depending on the severity of the error.</span></span> <span data-ttu-id="7bb45-115">İstek işlenirken bağlamında ileti izleme üzerinde iletisine çift tıklandığında getirir.</span><span class="sxs-lookup"><span data-stu-id="7bb45-115">Double-clicking on the message brings up the message trace in the context of the processing request.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7bb45-116">Bir ileti üst bilgisi yok, Hayır varsa `<header/>` etiketi günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="7bb45-116">If a message has no header, no `<header/>` tag is logged.</span></span>  
  
## <a name="viewing-messages-logged-by-a-client-a-relay-and-a-service"></a><span data-ttu-id="7bb45-117">Bir istemci, geçiş ve bir hizmet oturum açmış iletilerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="7bb45-117">Viewing Messages Logged by a Client, a Relay, and a Service</span></span>  
 <span data-ttu-id="7bb45-118">Ortamınızı sonradan yapılacak hizmetine ileten bir geçiş için bir ileti gönderen bir istemci içerebilir.</span><span class="sxs-lookup"><span data-stu-id="7bb45-118">Your environment may contain a client, which sends a message to a relay, that subsequently forwards the message to the service.</span></span> <span data-ttu-id="7bb45-119">Ne zaman ileti günlüğe kaydetme, tüm üç konumlarının etkinleştirildiğinde ve üç ileti günlüğü içinde görüntülenen [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) ileti günlüğü değişimleri yanlış eşzamanlı olarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="7bb45-119">When message logging is enabled on all three locations, and all three message logs are viewed in [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) simultaneously, the message log exchanges will be incorrectly rendered.</span></span> <span data-ttu-id="7bb45-120">Bunun nedeni, `CorrelationId` ve `ActivityId` ileti üstbilgisinde her send-receive çifti için benzersiz değil.</span><span class="sxs-lookup"><span data-stu-id="7bb45-120">This is because the `CorrelationId` and `ActivityId` in the Message header are not unique for every send-receive pair.</span></span>  
  
 <span data-ttu-id="7bb45-121">Bu sorunu çözmek için aşağıdaki yöntemlerden birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7bb45-121">You can use either one of the following methods to resolve this problem.</span></span>  
  
-   <span data-ttu-id="7bb45-122">Yalnızca iki üç ileti günlükleri görüntüleme [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) dilediğiniz zaman.</span><span class="sxs-lookup"><span data-stu-id="7bb45-122">Only view two of the three message logs in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) at any time.</span></span>  
  
-   <span data-ttu-id="7bb45-123">Üç tüm günlüklerde görüntülerseniz gerekir [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) aynı anda yeni bir geçiş hizmeti değiştirebilirsiniz <xref:System.ServiceModel.Channels.Message> örneği.</span><span class="sxs-lookup"><span data-stu-id="7bb45-123">If you must view all three logs in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) at the same time, you can modify the relay service by creating a new <xref:System.ServiceModel.Channels.Message> instance.</span></span> <span data-ttu-id="7bb45-124">Bu örnek hariç tüm üstbilgileri yanı sıra gelen ileti gövdesinin bir kopyasını olmalıdır `ActivityId` ve `Action` üstbilgileri.</span><span class="sxs-lookup"><span data-stu-id="7bb45-124">This instance should be a copy of the body of the incoming message, plus all the headers except for the `ActivityId` and `Action` headers.</span></span> <span data-ttu-id="7bb45-125">Aşağıdaki kod örneği, bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7bb45-125">The following example code demonstrates how to do this.</span></span>  
  
```  
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
  
## <a name="exceptional-cases-for-inaccurate-message-logging-content"></a><span data-ttu-id="7bb45-126">Olağanüstü durumlar için yanlış ileti günlüğe kaydetme içeriği</span><span class="sxs-lookup"><span data-stu-id="7bb45-126">Exceptional Cases for Inaccurate Message Logging Content</span></span>  
 <span data-ttu-id="7bb45-127">Aşağıdaki koşullarda iletileri günlüğe kaydedilmesini tam temsili sekizli akış kablo mevcut olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="7bb45-127">Under the following conditions, messages being logged might not be the exact representation of the octet stream present on the wire.</span></span>  
  
-   <span data-ttu-id="7bb45-128">Hiçbiri gelen / adres/içinde iletileri için BasicHttpBinding için zarf üst bilgileri günlüğe kaydedilen ad alanı.</span><span class="sxs-lookup"><span data-stu-id="7bb45-128">For BasicHttpBinding, envelope headers are logged for the incoming messages in the /addressing/none namespace.</span></span>  
  
-   <span data-ttu-id="7bb45-129">Boşluk eşleşmiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="7bb45-129">White spaces can be mismatched.</span></span>  
  
-   <span data-ttu-id="7bb45-130">Gelen iletiler için boş öğeleri farklı şekilde temsil edilebilir.</span><span class="sxs-lookup"><span data-stu-id="7bb45-130">For incoming messages, empty elements can be represented differently.</span></span> <span data-ttu-id="7bb45-131">Örneğin, \<etiket >\</etiketi > yerine \<etiket / ></span><span class="sxs-lookup"><span data-stu-id="7bb45-131">For example, \<tag>\</tag> instead of  \<tag/></span></span>  
  
-   <span data-ttu-id="7bb45-132">Bilinen PII günlüğü devre dışı bırakıldığında varsayılan veya açık ayarı enableLoggingKnownPii = "true".</span><span class="sxs-lookup"><span data-stu-id="7bb45-132">When known PII logging is disabled either by default or explicit setting enableLoggingKnownPii="true".</span></span>  
  
-   <span data-ttu-id="7bb45-133">Kodlama, UTF-8'e dönüştürme için etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="7bb45-133">Encoding is enabled for transforming to UTF-8.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bb45-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7bb45-134">See Also</span></span>  
 [<span data-ttu-id="7bb45-135">Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="7bb45-135">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)  
 [<span data-ttu-id="7bb45-136">İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma</span><span class="sxs-lookup"><span data-stu-id="7bb45-136">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [<span data-ttu-id="7bb45-137">Günlüğe İleti Kaydetme</span><span class="sxs-lookup"><span data-stu-id="7bb45-137">Message Logging</span></span>](../../../../docs/framework/wcf/diagnostics/message-logging.md)
