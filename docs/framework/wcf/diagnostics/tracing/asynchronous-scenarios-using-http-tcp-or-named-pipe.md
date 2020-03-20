---
title: HTTP, TCP veya Named-Pipe Kullanan Zaman Uyumsuz Senaryolar
ms.date: 03/30/2017
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
ms.openlocfilehash: 6ae96c0aac5010adf37eb78ed57d1549885ece58
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185781"
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a>HTTP, TCP veya Named-Pipe Kullanan Zaman Uyumsuz Senaryolar
Bu konu, http, TCP veya adlandırılmış boru kullanarak çok iş parçacığı istekleri ile farklı eşzamanlı istek/yanıt senaryoları için etkinlikleri ve aktarımları açıklar.  
  
## <a name="asynchronous-requestreply-without-errors"></a>Hatasız Asynchronous İstek/Yanıtla  
 Bu bölümde, çok iş parçacığı istemcileri olan bir eşzamanlı istek/yanıt senaryosu için etkinlikler ve aktarımlar açıklanır.  
  
 Arayan etkinliği `beginCall` döndüğünde sonlandırır `endCall` ve döndürür. Geri arama denirse, geri arama geri döner.  
  
 Çağrılan `beginCall` etkinlik, geri döndüğünde, `endCall` döndüğünde veya bu etkinlikten çağrıldığında geri arama geri döndüğünde sona erer.  
  
### <a name="asynchronous-client-without-callback"></a>Geri Arama olmadan Asynchronous İstemci  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a>Http kullanılarak Her İki Tarafta Da Yayılma Etkindir  
 ![PropagateActivity her iki tarafta doğru ayarlanmış hiçbir geri arama ile asynchronous istemci.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-no-callback.gif)
  
 Eğer `propagateActivity=true`, ProcessMessage hangi ProcessAction etkinliğine aktagerektiğini gösterir.  
  
 HTTP tabanlı senaryolar için ReceiveBytes gönderilecek ilk iletiye çağrılır ve isteğin kullanım ömrü boyunca vardır.  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a>Yayılma, HTTP kullanılarak Her Iki Tarafta Devre Dışı Bırakılır  
 Her `propagateActivity=false` iki tarafta ise, ProcessMessage hangi ProcessAction etkinliğine aktanınacak olduğunu göstermez. Bu nedenle, yeni bir kimlik içeren yeni bir geçici İşlem Eylemi etkinliği çağrılır. Eşzamanlı yanıt ServiceModel kodundaki istekle eşleştiğinde, Etkinlik Kimliği yerel bağlamdan alınabilir. Gerçek İşlem Eylem etkinliği bu kimlikle aktarılabilir.  
  
 ![PropagateActivity her iki tarafta yanlış olarak ayarlanmış hiçbir geri arama ile asynchronous istemci.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-either-side.gif)  

 HTTP tabanlı senaryolar için ReceiveBytes gönderilecek ilk iletiye çağrılır ve isteğin kullanım ömrü boyunca vardır.  
  
 Bir İşlem Eylem etkinliği, arayan veya callee'de ve `propagateActivity=false` yanıt iletisi eylem üstbilgisini içermediği zaman, eşzamanlı bir istemcide oluşturulur.  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a>TCP veya Adlandırılmış Boru Kullanılarak Her İki Tarafta Da Yayılma Etkindir  
 ![PropagateActivity'in her iki tarafta da doğru olarak ayarlandığı ve boru/TCP olarak adlandırılan geri aramasız asynchronous istemcisi.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-enabled-using-tcp.gif)  
  
 Adlandırılmış Boru veya TCP tabanlı bir senaryo için, istemci açıldığında ReceiveBytes çağrılır ve bağlantının ömrü boyunca var olur.  
  
 İlk görüntüye benzer `propagateActivity=true`şekilde, ProcessMessage hangi ProcessAction etkinliğine aktagerektiğini gösterirse.  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a>Yayılma, TCP veya Adlandırılmış Boru kullanılarak Her İki Tarafta Devre Dışı Bırakılır  
 Adlandırılmış Boru veya TCP tabanlı bir senaryo için, istemci açıldığında ReceiveBytes çağrılır ve bağlantının ömrü boyunca var olur.  
  
 İkinci görüntüye benzer `propagateActivity=false` şekilde, her iki tarafta ysa, ProcessMessage hangi ProcessAction etkinliğine aktanınacak olduğunu göstermez. Bu nedenle, yeni bir kimlik içeren yeni bir geçici İşlem Eylemi etkinliği çağrılır. Eşzamanlı yanıt ServiceModel kodundaki istekle eşleştiğinde, Etkinlik Kimliği yerel bağlamdan alınabilir. Gerçek İşlem Eylem etkinliği bu kimlikle aktarılabilir.  
  
 ![PropagateActivity'in her iki tarafta da false olarak ayarlandığı ve pipe/TCP adlı geri araması olmayan asynchronous istemci.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-using-tcp.gif)  

### <a name="asynchronous-client-with-callback"></a>Callback ile asynchronous istemcisi  
 Bu senaryo, geri arama ve , ve `endCall`bunların transferleri için G ve A', etkinlikleri ekler ve bunların içinde/dışında.  
  
 Bu bölümde sadece HTTP `propagateActivity` = `true`kullanarak gösterir . Ancak, ek etkinlikler ve aktarımlar diğer durumlar `propagateActivity` = `false`için de geçerlidir (diğer durumlarda (diğer bir deyişle, TCP veya Named-Pipe kullanarak).  
  
 Geri arama, istemci sonuçların hazır olduğunu bildirmek için kullanıcı kodunu aradığında yeni bir etkinlik (G) oluşturur. Kullanıcı kodu `endCall` daha sonra geri arama içinde (Şekil 5'te gösterildiği gibi) veya geri arama dışında (Şekil 6) çağırır. Hangi kullanıcı etkinliğinin `endCall` çağrıldığı bilinmedığından, bu etkinlik `A’`etiketlenir. A'nın A ile aynı veya A'dan farklı olması mümkündür.  
  
 ![Geri arama ile bir eşzamanlı istemci gösterir, geri arama da endcall.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-in-callback.gif)  

 ![Geri arama, geri arama dışında endcall ile bir eşzamanlı istemci gösterir.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-outside-callback.gif)  

### <a name="asynchronous-server-with-callback"></a>Geri Arama lı Asynchronous Server  
 ![Geri arama ile bir eşzamanlı sunucu gösterir.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-server-callback.gif)  

 Kanal yığını Ileti Alma'daki istemciyi geri çağırır: Bu işleme ait izler ProcessRequest etkinliğinin kendisine yayılır.  
  
## <a name="asynchronous-requestreply-with-errors"></a>Hatalarla Eşkron İstek/Yanıtla  
 Hata iletisi `endCall`hataları sırasında alınır. Aksi takdirde, etkinlikler ve aktarımlar önceki senaryolara benzer.  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a>Asynchronous One-Way veya Hatalar olmadan  
 İstemciye yanıt veya hata döndürülür.
