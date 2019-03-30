---
title: HTTP, TCP veya Named-Pipe Kullanan Eşzamanlı Senaryolar
ms.date: 03/30/2017
ms.assetid: 7e90af1b-f8f6-41b9-a63a-8490ada502b1
ms.openlocfilehash: 28e612b190f4993e1ce7da0d1083c4e55f827d4a
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654009"
---
# <a name="synchronous-scenarios-using-http-tcp-or-named-pipe"></a>HTTP, TCP veya Named-Pipe Kullanan Eşzamanlı Senaryolar
Bu konuda, HTTP, TCP kullanarak tek iş parçacıklı istemcisinde ile etkinlikleri ve aktarımları için farklı eşzamanlı istek/yanıt senaryoları açıklar veya adlandırılmış. Bkz: [HTTP, TCP veya Named-Pipe kullanan zaman uyumsuz senaryolar](../../../../../docs/framework/wcf/diagnostics/tracing/asynchronous-scenarios-using-http-tcp-or-named-pipe.md) çok iş parçacıklı istekleri hakkında daha fazla bilgi için.  
  
## <a name="synchronous-requestreply-without-errors"></a>Hatasız eşzamanlı istek/yanıt  
 Bu bölümde geçerli eş zamanlı istek/yanıt senaryosunda, tek iş parçacıklı istemci aktarımlarında ve etkinlikleri açıklar.  
  
### <a name="client"></a>İstemci  
  
#### <a name="establishing-communication-with-service-endpoint"></a>Hizmet uç noktası ile iletişim kurma  
 Bir istemci oluşturulur ve açılır. Bu adımların her biri için çevresel etkinliği bir "İstemci oluşturmak" (B) ve "İstemcisini açın" (C) etkinliği için sırasıyla aktarılır (A). Oluncaya kadar aktarım geri, diğer bir deyişle, ServiceModel kod yürütülene kadar için aktarılan her etkinlik için ortam etkinlik askıya alındı.  
  
#### <a name="making-a-request-to-service-endpoint"></a>Hizmet uç noktası için bir istekte  
 Ortam etkinliği için bir "ProcessAction" (D) etkinliği aktarılır. Bu etkinlik içinde bir istek iletisi gönderilir ve bir yanıt iletisi aldı. Denetim için kullanıcı kodu döndürdüğünde etkinlik sona erer. Bu eşzamanlı isteği olduğundan, ortam etkinlik denetim dönene kadar askıya alır.  
  
#### <a name="closing-communication-with-service-endpoint"></a>Hizmet uç noktası ile iletişim kapatma  
 İstemci etkinliği Kapat (ı) ortam etkinliğinden oluşturulur. Bu, yeni ve açık aynıdır.  
  
### <a name="server"></a>Sunucu  
  
#### <a name="setting-up-a-service-host"></a>Bir hizmet konağı ayarlama  
 ServiceHost'ın açık ve yeni etkinlikleri (N ve O) ortam etkinliğinden (M) oluşturulur.  
  
 Her dinleyici için bir ServiceHost açmasını dinleyici etkinlik (P) oluşturulur. Dinleyici etkinlik almak ve veri işlemek için bekler.  
  
#### <a name="receiving-data-on-the-wire"></a>Kablo verileri alma  
 Kablo verileri ulaşır ulaşmaz "ReceiveBytes" etkinlik (Q) alınan verileri işlemek için zaten yoksa, oluşturulur. Bu etkinlik bir bağlantı veya sıra içinde birden çok ileti için yeniden kullanılabilir.  
  
 SOAP eylemi iletisi oluşturmak için yeterli veri yoksa ReceiveBytes etkinlik ProcessMessage etkinlik (R) başlatır.  
  
 Etkinlik R, ileti üst işlenir ve etkinlik kimliği üst bilgisi doğrulandı. Bu üst bilgi varsa, etkinlik kimliği ProcessAction etkinliği ayarlanır; Aksi takdirde, yeni bir kimlik oluşturulur.  
  
 ProcessAction etkinlik (S) oluşturulur ve için aktarılmakta olan çağrı zaman işlenir. Gelen iletinin ilgili tüm işlemler tamamlandığında (T) kullanıcı kodunun yürütülmesi ve yanıt iletisini göndermeyi dahil olmak üzere bu etkinlik sona erer.  
  
#### <a name="closing-a-service-host"></a>Bir hizmet konağı  
 ServiceHost'ın Kapat etkinlik (Z), ortam etkinliğinden oluşturulur.  
  
 ![Eşzamanlı senaryolar gösteren diyagram: HTTP, TCP veya adlandırılmış kanallar.](./media/synchronous-scenarios-using-http-tcp-or-named-pipe/synchronous-scenario-http-tcp-named-pipes.gif)  
  
 İçinde \<y: adı >, `A` önceki metni hem de tablosunda 3 etkinliği açıklayan bir kısayol semboldür. `Name` Etkinliğin kısaltılmış bir addır.  
  
 Varsa `propagateActivity` = `true`, hem istemci hem de hizmet işlemi eyleme sahip aynı etkinlik kimliği  
  
## <a name="synchronous-requestreply-with-errors"></a>Hatalarla eşzamanlı istek/yanıt  
 Önceki senaryonun tek farkı, bir SOAP hatası iletisi bir yanıt iletisi olarak döndürülür. Varsa `propagateActivity` = `true`, etkinlik kimliği istek iletisinin SOAP hatası iletiye eklenir.  
  
## <a name="synchronous-one-way-without-errors"></a>Zaman uyumlu hatasız tek yönlü  
 İlk senaryo tek fark, ileti sunucuya döndürülür. Bir durum HTTP tabanlı protokoller için (geçerli veya hata) hala istemciye döndürülür. HTTP WCF protokol yığınının bir parçası olan bir istek-yanıt semantiğine sahip tek protokoldür olmasıdır. WCF TCP işleme gizlenmiş olduğundan, istemciye hiçbir bildirim gönderilir.  
  
## <a name="synchronous-one-way-with-errors"></a>Zaman uyumlu hatalarla tek yönlü  
 İleti işlenirken bir hata oluşursa (soru veya sonrasını), herhangi bir bildirimi, istemciye döndürülür. Bu "Zaman uyumlu One-Way olmadan hatalarını" senaryosuna benzer. Bir hata iletisini almak istemiyorsanız, tek yönlü bir senaryoda kullanmamanız gerekir.  
  
## <a name="duplex"></a>Çift Yönlü  
 Önceki senaryoları ile istemci ReceiveBytes ve ProcessMessage etkinlikleri, zaman uyumsuz senaryolar için benzer oluşturur, bir hizmet olarak davranan farktır.
