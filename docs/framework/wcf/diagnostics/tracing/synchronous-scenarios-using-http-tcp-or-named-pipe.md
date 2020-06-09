---
title: HTTP, TCP veya Named-Pipe Kullanan Eşzamanlı Senaryolar
ms.date: 03/30/2017
ms.assetid: 7e90af1b-f8f6-41b9-a63a-8490ada502b1
ms.openlocfilehash: 662067fc5564c9421ce24b28b291d06690b129ea
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589190"
---
# <a name="synchronous-scenarios-using-http-tcp-or-named-pipe"></a>HTTP, TCP veya Named-Pipe Kullanan Eşzamanlı Senaryolar
Bu konuda, HTTP, TCP veya adlandırılmış kanal kullanarak, tek iş parçacıklı bir istemciyle farklı zaman uyumlu istek/yanıt senaryolarına yönelik etkinlikler ve aktarımlar açıklanmaktadır. Çoklu iş parçacıklı istekler hakkında daha fazla bilgi için bkz. [http, TCP veya Named-Pipe kullanan zaman uyumsuz senaryolar](asynchronous-scenarios-using-http-tcp-or-named-pipe.md) .  
  
## <a name="synchronous-requestreply-without-errors"></a>Hata olmadan zaman uyumlu Istek/yanıt  
 Bu bölümde, tek iş parçacıklı istemciyle geçerli bir zaman uyumlu istek/yanıt senaryosuna yönelik etkinlikler ve aktarımlar açıklanmaktadır.  
  
### <a name="client"></a>İstemci  
  
#### <a name="establishing-communication-with-service-endpoint"></a>Hizmet uç noktası ile Iletişim kurma  
 İstemci oluşturulur ve açılır. Bu adımların her biri için, çevresel etkinlik (A) sırasıyla bir "yapı Istemcisi" (B) ve "açık Istemci" (C) etkinliğine aktarılır. Aktarılmakta olan her etkinlik için, bir aktarım geri alınana kadar, diğer bir deyişle, ServiceModel kodu yürütülene kadar çevresel etkinlik askıya alınır.  
  
#### <a name="making-a-request-to-service-endpoint"></a>Hizmet uç noktasına Istek yapılıyor  
 Çevresel etkinlik bir "ProcessAction" (D) etkinliğine aktarılır. Bu etkinlik dahilinde bir istek iletisi gönderilir ve bir yanıt iletisi alınır. Denetim Kullanıcı koduna döndüğünde etkinlik sona erer. Bu zaman uyumlu bir istek olduğundan, ortam etkinliği denetim tarafından dönüşene kadar askıya alınır.  
  
#### <a name="closing-communication-with-service-endpoint"></a>Hizmet uç noktası ile Iletişim kapatılıyor  
 İstemci kapatma etkinliği (I) çevresel etkinlikten oluşturulur. Bu, New ve Open ile aynıdır.  
  
### <a name="server"></a>Sunucu  
  
#### <a name="setting-up-a-service-host"></a>Hizmet ana bilgisayarı ayarlama  
 ServiceHost 'un yeni ve açık Etkinlikleri (N ve O) çevresel etkinlikten (M) oluşturulur.  
  
 Her dinleyici için bir ServiceHost açılmadan bir dinleyici etkinliği (P) oluşturulur. Dinleyici etkinliği verileri almak ve işlemek için bekler.  
  
#### <a name="receiving-data-on-the-wire"></a>Hattaki verileri alma  
 Veriler kabloya ulaştığında, alınan verileri işlemek için zaten mevcut değilse (Q) bir "ReceiveBytes" etkinliği oluşturulur. Bu etkinlik bir bağlantı veya kuyruk içindeki birden çok ileti için yeniden kullanılabilir.  
  
 Bir SOAP eylem iletisi oluşturmak için yeterli veri varsa, ReceiveBytes etkinliği bir ProcessMessage etkinliği (R) başlatır.  
  
 Etkinlik R ' de ileti üstbilgileri işlenir ve ActivityId üst bilgisi doğrulanır. Bu üst bilgi varsa, etkinlik KIMLIĞI ProcessAction etkinliğine ayarlanır; Aksi takdirde, yeni bir KIMLIK oluşturulur.  
  
 Çağrı işlendiğinde ProcessAction etkinlikleri oluşturulur ve ' a aktarılır. Bu etkinlik, Kullanıcı kodu (T) yürütülüyor ve uygunsa yanıt iletisini gönderme dahil olmak üzere, gelen iletiyle ilgili tüm işlemler tamamlandığında sona erer.  
  
#### <a name="closing-a-service-host"></a>Hizmet konağını kapatma  
 ServiceHost 'un Close etkinliği (Z) çevresel etkinlikten oluşturulur.  
  
 ![Zaman uyumlu senaryoları gösteren diyagram: HTTP, TCP veya adlandırılmış kanallar.](./media/synchronous-scenarios-using-http-tcp-or-named-pipe/synchronous-scenario-http-tcp-named-pipes.gif)  
  
 İçinde \<A: name> , `A` önceki metinde ve tablo 3 ' te etkinliği açıklayan bir kısayol simgedir. `Name`etkinliğin kısaltılmış bir adıdır.  
  
 Eğer `propagateActivity` = `true` , hem istemci hem de hizmette işlem eylemi aynı etkinlik kimliğine sahiptir.  
  
## <a name="synchronous-requestreply-with-errors"></a>Zaman uyumlu Istek/hatalarla yanıtla  
 Önceki senaryoya ilişkin tek fark, bir SOAP hata iletisinin yanıt iletisi olarak döndürüldüğünden olur. İse `propagateActivity` = `true` , istek iletisinin etkinlik kimliği SOAP hata iletisine eklenir.  
  
## <a name="synchronous-one-way-without-errors"></a>Hata olmadan zaman uyumlu tek yönlü  
 İlk senaryoya göre tek fark, sunucuya hiçbir ileti döndürülmüyor. HTTP tabanlı protokoller için istemciye bir durum (geçerli veya hata) döndürülmeye devam edilir. Bunun nedeni, HTTP 'nin WCF protokol yığınının parçası olan bir istek-yanıt semantiğinin bulunduğu tek protokoldür. TCP işlemi WCF 'den gizlendiğinden, istemciye hiçbir onay gönderilmez.  
  
## <a name="synchronous-one-way-with-errors"></a>Hatalı eşzamanlı tek yönlü  
 İleti işlenirken bir hata oluşursa (Q veya daha fazla), istemciye hiçbir bildirim döndürülmez. Bu, "hatasız eşzamanlı tek yönlü" senaryo ile aynıdır. Bir hata iletisi almak istiyorsanız tek yönlü bir senaryo kullanmamalısınız.  
  
## <a name="duplex"></a>Çift Yönlü  
 Önceki senaryolarla aradaki fark, istemcinin zaman uyumsuz senaryolara benzer şekilde ReceiveBytes ve ProcessMessage etkinlikleri oluşturduğu bir hizmet olarak davranmasıdır.
