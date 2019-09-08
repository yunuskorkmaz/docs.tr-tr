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
# <a name="viewing-message-logs"></a>İleti Günlüklerini Görüntüleme
Bu konu başlığı altında, ileti günlüklerini nasıl görüntüleyebileceğiniz açıklanmaktadır.  
  
## <a name="viewing-message-logs-in-the-service-trace-viewer"></a>Hizmet Izleme görüntüleyicisinde Ileti günlüklerini görüntüleme  
 WCF tarafından işlendiği için bir ileti dönüştürülür. Bu nedenle, günlüğe kaydedilen bir ileti, iletideki içeriği değil, yalnızca iletinin günlüğe kaydedildiği noktada yansıtır.  
  
 İleti günlüğe kaydetme çıkışında iletinin aktarım biçimiyle hiçbir ilişki bulunmadığından, ileti günlüğü her zaman kodu çözülen iletiyi verir. İleti günlüğe kaydetmeyi doğru şekilde yapılandırdıysanız, günlüğe kaydedilen tüm iletiler düz metin biçiminde olmalıdır. Örneğin, günlüğe kaydedilen iletilerin biçimi (düz metin) bir ikili ileti Kodlayıcısı kullanımından etkilenmez.  
  
 XmlWriterTraceListener çıkışı, XML parçaları dizisi içeren bir dosyadır. Dosyanın geçerli bir XML dosyası olmadığı farkında olmalısınız. İleti günlüğü dosyalarını görüntülemek için [hizmet Izleme Görüntüleyicisi aracı 'nı (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) kullanmanız önerilir. Bu aracın nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [Ilişkili izlemeleri ve sorun gidermeyi görüntülemek Için hizmet Izleme görüntüleyicisini kullanma](./tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
 Hizmet Izleme görüntüleyicisinde iletiler **ileti** sekmesinde listelenir. Oluşan veya ilişkili olan iletiler, hatanın önem derecesine bağlı olarak bir işleme hatası sarı (uyarı düzeyi) veya kırmızı (hata düzeyi) olarak vurgulanır. İletiye çift tıklamak, işleme isteği bağlamında ileti izlemeyi getirir.  
  
> [!NOTE]
> Bir iletinin üstbilgisi yoksa, hiçbir `<header/>` etiket kaydedilmez.  
  
## <a name="viewing-messages-logged-by-a-client-a-relay-and-a-service"></a>Istemci, geçiş ve hizmet tarafından günlüğe kaydedilen Iletileri görüntüleme  
 Ortamınız, daha sonra iletiyi hizmete ileten bir geçişe ileti gönderen bir istemci içeriyor olabilir. Her üç konumda ileti günlüğe kaydetme etkin olduğunda ve üç ileti günlüğü de [hizmet Izleme Görüntüleyicisi Aracı (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) içinde aynı anda görüntülendiğinde, ileti günlüğü alışverişleri yanlış işlenir. Bunun nedeni, ileti `CorrelationId` üstbilgisindeki `ActivityId` ve içindeki her gönderme alma çiftinin benzersiz olmaması nedeniyle oluşur.  
  
 Bu sorunu çözmek için aşağıdaki yöntemlerden birini kullanabilirsiniz.  
  
- [Hizmet Izleme Görüntüleyicisi Aracı (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) içindeki üç ileti günlüğünün ikisini de her zaman görüntüleyin.  
  
- [Hizmet izleme Görüntüleyicisi aracında (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) tüm üç günlüğü aynı anda görüntülemeniz gerekiyorsa, yeni <xref:System.ServiceModel.Channels.Message> bir örnek oluşturarak geçiş hizmetini değiştirebilirsiniz. Bu örnek, gelen ileti gövdesinin bir kopyası olmalıdır `ActivityId` ve ve `Action` üst bilgileri hariç tüm üst bilgileri içermelidir. Aşağıdaki örnek kodda bunun nasıl yapılacağı gösterilmektedir.  
  
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
  
## <a name="exceptional-cases-for-inaccurate-message-logging-content"></a>Hatalı Ileti günlüğü Içeriği için olağanüstü durumlar  
 Aşağıdaki koşullarda günlüğe yazılan iletiler, tel üzerinde mevcut olan sekizli akışın tam temsili olmayabilir.  
  
- BasicHttpBinding için,/Addressing/None ad alanındaki gelen iletiler için zarf üstbilgileri günlüğe kaydedilir.  
  
- Boşluk, uyumsuz olabilir.  
  
- Gelen iletilerde boş öğeler farklı gösterilebilir. Örneğin, \<etiket/>\<yerine \<etiket >/Tag >  
  
- Bilinen PII günlüğü varsayılan olarak devre dışı bırakıldığında ya da enableLoggingKnownPII = "true" ayarını Açık olarak ayarlar.  
  
- Kodlama UTF-8 ' e dönüştürmek için etkinleştirilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)
- [İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma](./tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Günlüğe İleti Kaydetme](message-logging.md)
