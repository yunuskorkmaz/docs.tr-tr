---
description: 'Daha fazla bilgi edinin: HTTP, TCP veya Named-Pipe kullanan zaman uyumsuz senaryolar'
title: HTTP, TCP veya Named-Pipe Kullanan Zaman Uyumsuz Senaryolar
ms.date: 03/30/2017
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
ms.openlocfilehash: 5e01866cd20d63796741a097a6d7d774ea45d3d9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99770956"
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a>HTTP, TCP veya Named-Pipe Kullanan Zaman Uyumsuz Senaryolar

Bu konuda, HTTP, TCP veya adlandırılmış kanal kullanan çok iş parçacıklı istekler ile farklı zaman uyumsuz istek/yanıt senaryolarına yönelik etkinlikler ve aktarımlar açıklanmaktadır.  
  
## <a name="asynchronous-requestreply-without-errors"></a>Hata olmadan zaman uyumsuz Istek/yanıt  

 Bu bölümde, çok iş parçacıklı istemcilerle zaman uyumsuz istek/yanıt senaryosuna yönelik etkinlikler ve aktarımlar açıklanmaktadır.  
  
 Çağıran etkinlik, döndüğünde sonlanır `beginCall` ve `endCall` döndürür. Bir geri çağırma çağrılırsa geri arama döndürülür.  
  
 Çağrılan etkinlik, döndürüldüğünde `beginCall` , `endCall` döndüğünde veya geri çağırma, Bu etkinlikten çağrıldıysa döndürülür.  
  
### <a name="asynchronous-client-without-callback"></a>Geri çağırma olmadan zaman uyumsuz Istemci  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a>Yayma, HTTP kullanarak her Iki tarafta da etkindir  

 ![PropagateActivity her iki tarafta da true olarak ayarlandığında, geri arama olmadan zaman uyumsuz istemci.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-no-callback.gif)
  
 Eğer `propagateActivity=true` , ProcessMessage hangi ProcessAction etkinliğinin aktarılacağı anlamına gelir.  
  
 HTTP tabanlı senaryolar için, gönderilen ilk ileti üzerinde ReceiveBytes çağrılır ve isteğin ömrü için mevcut olur.  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a>Yayma, HTTP kullanarak her Iki tarafta da devre dışı bırakıldı  

 `propagateActivity=false`İki taraftan, ProcessMessage, hangi ProcessAction etkinliğinin aktarılacağı anlamına gelmez. Bu nedenle, yeni KIMLIĞE sahip yeni bir geçici ProcessAction etkinliği çağırılır. Zaman uyumsuz yanıt, ServiceModel kodundaki istekle eşleştiğinde, etkinlik KIMLIĞI Yerel içerikten alınabilir. Gerçek ProcessAction etkinliği bu KIMLIKLE öğesine aktarılabilir.  
  
 ![PropagateActivity her iki tarafta da false olarak ayarlandığında, geri çağırması olmayan zaman uyumsuz istemci.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-either-side.gif)  

 HTTP tabanlı senaryolar için, gönderilen ilk ileti üzerinde ReceiveBytes çağrılır ve isteğin ömrü için mevcut olur.  
  
 Bir Işlem eylemi etkinliği, çağıran veya çağrılan zaman uyumsuz bir istemcide oluşturulur `propagateActivity=false` ve yanıt iletisi bir eylem üst bilgisi içermez.  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a>Yayılma, TCP veya adlandırılmış kanal kullanılarak her Iki tarafta de etkinleştirilir  

 ![PropagateActivity her iki tarafta da true, ve adlandırılmış kanal/TCP olarak ayarlandığı zaman uyumsuz istemci geri çağırması yok.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-enabled-using-tcp.gif)  
  
 Named-Pipe veya TCP tabanlı bir senaryoda, istemci açıldığında ReceiveBytes çağrılır ve bağlantı ömrü boyunca mevcut olur.  
  
 İlk resme benzer şekilde, `propagateActivity=true` ProcessMessage, hangi ProcessAction etkinliğinin aktarılacağı anlamına gelir.  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a>Yayma, TCP veya adlandırılmış kanal kullanılarak Iki tarafta da devre dışı bırakıldı  

 Named-Pipe veya TCP tabanlı bir senaryoda, istemci açıldığında ReceiveBytes çağrılır ve bağlantı ömrü boyunca mevcut olur.  
  
 İkinci görüntüye benzer şekilde, `propagateActivity=false` her iki tarafta de ProcessMessage, hangi ProcessAction etkinliğinin aktarılacağı anlamına gelmez. Bu nedenle, yeni KIMLIĞE sahip yeni bir geçici ProcessAction etkinliği çağırılır. Zaman uyumsuz yanıt, ServiceModel kodundaki istekle eşleştiğinde, etkinlik KIMLIĞI Yerel içerikten alınabilir. Gerçek ProcessAction etkinliği bu KIMLIKLE öğesine aktarılabilir.  
  
 ![PropagateActivity her iki tarafta ve adlandırılmış kanal/TCP 'de yanlış olarak ayarlandığı hiçbir geri arama olmadan zaman uyumsuz istemci.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-using-tcp.gif)  

### <a name="asynchronous-client-with-callback"></a>Geri çağırma ile zaman uyumsuz istemci  

 Bu senaryo, geri çağırma için ve `endCall` , ve bunların aktarımları içindeki/giden etkinliklere G ve A ' yı ekler.  
  
 Bu bölüm yalnızca ile HTTP kullanımını gösterir `propagateActivity` = `true` . Ancak, ek etkinlikler ve aktarımlar diğer durumlar için de geçerlidir (yani, `propagateActivity` = `false` TCP veya adlandırılmış kanal kullanarak).  
  
 Geri arama, istemci, sonuçların hazırlandığını bildirmek için Kullanıcı kodunu çağırdığında yeni bir etkinlik (G) oluşturur. Kullanıcı kodu daha sonra `endCall` geri çağırma içinde (Şekil 5 ' te gösterildiği gibi) veya geri çağırma dışında çağırır (Şekil 6). Hangi kullanıcı etkinliğinin `endCall` çağrıldığı bilinmiyor, bu etkinlik etiketlidir `A’` . ' Bir ' ile aynı veya arasında farklı olabilir.  
  
 ![Geri çağırma ile zaman uyumsuz bir istemciyi gösterir, geri çağırma sırasında endCall.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-in-callback.gif)  

 ![Geri çağırma, geri çağırma dışında zaman uyumsuz bir istemciyi gösterir.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-outside-callback.gif)  

### <a name="asynchronous-server-with-callback"></a>Geri çağırma ile zaman uyumsuz sunucu  

 ![Geri çağırma ile zaman uyumsuz bir sunucu gösterir.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-server-callback.gif)  

 Kanal yığını istemciyi geri çağırır Ileti alma: Bu işleme yönelik izlemeler, ProcessRequest etkinliğinin kendisidir.  
  
## <a name="asynchronous-requestreply-with-errors"></a>Zaman uyumsuz Istek/hatalarla yanıtla  

 Hata iletisi hataları sırasında alınır `endCall` . Aksi takdirde, etkinlikler ve aktarımlar önceki senaryolara benzerdir.  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a>Hatasız veya hata olmadan zaman uyumsuz One-Way  

 İstemciye yanıt veya hata döndürülmez.
