---
title: "HTTP, TCP veya Named-Pipe Kullanan Eşzamanlı Senaryolar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e90af1b-f8f6-41b9-a63a-8490ada502b1
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 428e8852c9b1706e88b1688b4a1f2e36c167fe28
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="synchronous-scenarios-using-http-tcp-or-named-pipe"></a>HTTP, TCP veya Named-Pipe Kullanan Eşzamanlı Senaryolar
Bu konuda veya adlandırılmış etkinlikleri ve aktarımlar farklı eşzamanlı istek/yanıt senaryoları için HTTP, TCP kullanan bir tek iş parçacıklı istemci ile açıklanır. Bkz: [zaman uyumsuz HTTP, TCP veya Named-Pipe kullanan senaryolar](../../../../../docs/framework/wcf/diagnostics/tracing/asynchronous-scenarios-using-http-tcp-or-named-pipe.md) çok iş parçacıklı istekleri hakkında daha fazla bilgi için.  
  
## <a name="synchronous-requestreply-without-errors"></a>Eşzamanlı istek/yanıt hatasız  
 Bu bölümde, etkinlikleri ve aktarımlar için tek iş parçacıklı istemci ile bir geçerli eşzamanlı istek/yanıt senaryo açıklanmaktadır.  
  
### <a name="client"></a>İstemci  
  
#### <a name="establishing-communication-with-service-endpoint"></a>Hizmet uç noktası ile iletişim kurma  
 Bir istemci oluşturulan ve açılır. Bu adımların her biri için ortam etkinliği bir "İstemci oluşturmak" (B) ve "Açık istemci" (C) etkinliğe sırasıyla aktarılır (A). Oluncaya kadar bir aktarımı geri, diğer bir deyişle, ServiceModel kod yürütülene dek için aktarılan her etkinlik için ortam etkinliği askıya alınır.  
  
#### <a name="making-a-request-to-service-endpoint"></a>Hizmet uç noktasına istekte  
 Ortam etkinliği için "ProcessAction" (D) etkinlik aktarılır. Bu etkinlik bir istek iletisi gönderilir ve bir yanıt iletisi aldı. Denetim için kullanıcı kodu döndürdüğünde etkinliği sona erer. Zaman uyumlu bir isteği gerektiğinden denetim dönene kadar ortam etkinliği askıya alır.  
  
#### <a name="closing-communication-with-service-endpoint"></a>Hizmet uç noktası ile iletişim kapatma  
 Kapat etkinlik istemcinin (ı) ortam etkinliğinden oluşturulur. Bu yeni ve açık için aynıdır.  
  
### <a name="server"></a>Sunucu  
  
#### <a name="setting-up-a-service-host"></a>Hizmet ana bilgisayarı ayarlama  
 ServiceHost'ın açık ve yeni etkinlikler (N ve O) ortam etkinliğinden (M) oluşturulur.  
  
 Dinleyici etkinlik (P), her dinleyici için bir ServiceHost açmasını oluşturulur. Dinleyici etkinlik almak ve verileri işlemek için bekler.  
  
#### <a name="receiving-data-on-the-wire"></a>Hat üzerinde veri alma  
 Veri kablo ulaştığında, bir "ReceiveBytes" etkinliği alınan verileri işlemek için (Q) zaten yoksa, oluşturulur. Bu etkinlik için bir bağlantı veya sıra içinde birden fazla ileti yeniden kullanılabilir.  
  
 SOAP eylemi iletisi oluşturmak için yeterli veri varsa ReceiveBytes etkinlik ProcessMessage etkinlik (R) başlatır.  
  
 Etkinlik R, ileti üstbilgilerini işlenir ve ActivityID üst bilgisi doğrulandı. Bu üst varsa, etkinlik kimliği ProcessAction etkinlik ayarlanır; Aksi takdirde, yeni bir kimliği oluşturulur.  
  
 ProcessAction etkinlik (S) oluşturulur ve için aktarılan, çağrı zaman işlenir. Kullanıcı kodu (T) yürütme ve yanıt iletisini göndermeyi dahil olmak üzere gelen iletiyle ilgili tüm işlem tamamlandığında, bu etkinliği sona erer.  
  
#### <a name="closing-a-service-host"></a>Hizmet ana bilgisayarını kapatma  
 ServiceHost'ın Kapat etkinlik (Z) ortam etkinliğinden oluşturulur.  
  
 ![HTTP &#47;kullanan eşzamanlı senaryolar; TCP &#47; Adlandırılmış Kanallar](../../../../../docs/framework/wcf/diagnostics/tracing/media/sync.gif "eşitleme")  
  
 İçinde \<A: adı >, `A` önceki metin ve Tablo 3 etkinliği açıklayan bir kısayol simge. `Name`Etkinliğin kısaltılmış bir addır.  
  
 Varsa `propagateActivity` = `true`, hem istemci hem de hizmet işlemi eylem sahip aynı etkinlik kimliği  
  
## <a name="synchronous-requestreply-with-errors"></a>Eşzamanlı istek/yanıt hatalı  
 Önceki senaryoda tek fark, bir SOAP hatası iletisi bir yanıt iletisi döndürülür. Varsa `propagateActivity` = `true`, etkinlik kimliği istek iletisinin SOAP hata iletisi eklenir.  
  
## <a name="synchronous-one-way-without-errors"></a>Zaman uyumlu hatasız tek yönlü  
 İlk senaryo ile tek fark, hiçbir ileti sunucuya döndürülür. HTTP tabanlı protokolleri, bir durum için (geçerli veya hata) hala istemciye döndürülür. HTTP parçası olan bir istek-yanıt semantiği ile tek protokoldür olmasıdır [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] protokol yığını. TCP işleme gizli olduğu [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)], onay istemciye gönderilir.  
  
## <a name="synchronous-one-way-with-errors"></a>Zaman uyumlu hatalarla tek yönlü  
 İleti işlenirken bir hata meydana gelirse (Q veya sonrasını), bildirim istemciye döndürülür. Bu, "Zaman uyumlu One-Way olmadan hataları" senaryo ile aynıdır. Bir hata iletisi almak istiyorsanız, tek yönlü bir senaryo kullanmamanız gerekir.  
  
## <a name="duplex"></a>Çift Yönlü  
 Önceki senaryoları ile istemci ReceiveBytes ve ProcessMessage etkinlikleri için zaman uyumsuz senaryolar benzer oluşturan bir hizmet olarak davranan farktır.
