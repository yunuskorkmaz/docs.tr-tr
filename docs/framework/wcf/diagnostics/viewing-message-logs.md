---
title: İleti Günlüklerini Görüntüleme
ms.date: 03/30/2017
ms.assetid: 3012fa13-f650-45fb-aaea-c5cca8c7d372
ms.openlocfilehash: 5e72aef7addb1e517bdf8cab4e300f6f8df5f833
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662829"
---
# <a name="viewing-message-logs"></a>İleti Günlüklerini Görüntüleme
Bu konu, ileti günlüklerini görüntüleme biçimini açıklar.  
  
## <a name="viewing-message-logs-in-the-service-trace-viewer"></a>İleti görüntüleme hizmet izleme Görüntüleyicisi'nde günlüğe kaydeder  
 WCF tarafından işlendiği bir ileti dönüştürülür. Bu nedenle, bir ileti günlüğe kaydedildi. yalnızca ileti içeriği, günlüğe kaydedilen noktasına değil Tel üzerinde içerik yansıtır.  
  
 Günlüğe ileti kaydetme çıktısını iletisinin aktarımı biçimi hiçbir ilişkisi olduğundan, her zaman ileti günlüğe kaydetme kodu çözülen ileti çıkarır. İletileri günlüğe düzgün şekilde yapılandırdıysanız, günlüğe kaydedilen iletiler düz metin biçiminde olmalıdır. Örneğin, günlüğe kaydedilen iletilere biçimi (düz metin), ikili ileti Kodlayıcısı'nın kullanımı etkilenmez.  
  
 XmlWriterTraceListener çıktısını bir dizi parçalarını içeren bir dosyadır. Dosya geçerli bir XML dosyası değil bilmeniz gerekir. Kullanmanız önerilir [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) ileti günlük dosyalarını görüntülemek için. Bu aracı kullanma hakkında daha fazla bilgi için bkz. [ilişkilendirilmiş izlemeleri görüntülemek ve sorun giderme için hizmet izleme görüntüleyicisini kullanarak](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
 Hizmet izleme Görüntüleyicisi'nde iletileri içinde listelenen **ileti** sekmesi. Neden veya olmayan iletilerini ilgili işleme hatası (uyarı düzeyi), sarı veya kırmızı (hata düzeyi), hatanın önem derecesine bağlı olarak vurgulanır. İstek işlenirken bağlamında ileti izleme üzerinde iletisine çift tıklandığında getirir.  
  
> [!NOTE]
>  Bir ileti üst bilgisi yok, Hayır varsa `<header/>` etiketi günlüğe kaydedilir.  
  
## <a name="viewing-messages-logged-by-a-client-a-relay-and-a-service"></a>Bir istemci, geçiş ve bir hizmet oturum açmış iletilerini görüntüleme  
 Ortamınızı sonradan yapılacak hizmetine ileten bir geçiş için bir ileti gönderen bir istemci içerebilir. Ne zaman ileti günlüğe kaydetme, tüm üç konumlarının etkinleştirildiğinde ve üç ileti günlüğü içinde görüntülenen [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) ileti günlüğü değişimleri yanlış eşzamanlı olarak işlenir. Bunun nedeni, `CorrelationId` ve `ActivityId` ileti üstbilgisinde her send-receive çifti için benzersiz değil.  
  
 Bu sorunu çözmek için aşağıdaki yöntemlerden birini kullanabilirsiniz.  
  
- Yalnızca iki üç ileti günlükleri görüntüleme [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) dilediğiniz zaman.  
  
- Üç tüm günlüklerde görüntülerseniz gerekir [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) aynı anda yeni bir geçiş hizmeti değiştirebilirsiniz <xref:System.ServiceModel.Channels.Message> örneği. Bu örnek hariç tüm üstbilgileri yanı sıra gelen ileti gövdesinin bir kopyasını olmalıdır `ActivityId` ve `Action` üstbilgileri. Aşağıdaki kod örneği, bunun nasıl yapılacağı gösterilmektedir.  
  
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
  
## <a name="exceptional-cases-for-inaccurate-message-logging-content"></a>Olağanüstü durumlar için yanlış ileti günlüğe kaydetme içeriği  
 Aşağıdaki koşullarda iletileri günlüğe kaydedilmesini tam temsili sekizli akış kablo mevcut olmayabilir.  
  
- Hiçbiri gelen / adres/içinde iletileri için BasicHttpBinding için zarf üst bilgileri günlüğe kaydedilen ad alanı.  
  
- Boşluk eşleşmiyor olabilir.  
  
- Gelen iletiler için boş öğeleri farklı şekilde temsil edilebilir. Örneğin, \<etiket >\</etiketi > yerine \<etiket / >  
  
- Bilinen PII günlüğü devre dışı bırakıldığında varsayılan veya açık ayarı enableLoggingKnownPii = "true".  
  
- Kodlama, UTF-8'e dönüştürme için etkinleştirilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
- [İlişkilendirilmiş İzlemeleri Görüntülemek ve Sorun Gidermek için Hizmet İzleme Görüntüleyicisini Kullanma](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Günlüğe İleti Kaydetme](../../../../docs/framework/wcf/diagnostics/message-logging.md)
