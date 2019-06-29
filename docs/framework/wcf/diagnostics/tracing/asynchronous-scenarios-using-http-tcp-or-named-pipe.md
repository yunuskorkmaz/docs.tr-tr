---
title: HTTP, TCP veya Named-Pipe Kullanan Zaman Uyumsuz Senaryolar
ms.date: 03/30/2017
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
ms.openlocfilehash: 218887f7d09e234d0d02dfa1df5c1d4e114ddc11
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422233"
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a>HTTP, TCP veya Named-Pipe Kullanan Zaman Uyumsuz Senaryolar
Bu konuda etkinlikler ve aktarımları farklı zaman uyumsuz istek/yanıt senaryoları için TCP ve HTTP kullanarak birden çok iş parçacıklı isteklerle açıklar veya adlandırılmış.  
  
## <a name="asynchronous-requestreply-without-errors"></a>Zaman uyumsuz istek/yanıt hatasız  
 Bu bölümde, etkinlikleri ve aktarımlar için birden çok iş parçacıklı istemcilerle bir zaman uyumsuz istek/yanıt senaryosu açıklanmaktadır.  
  
 Arayan etkinlik ne zaman sona erer `beginCall` döndürür, ve `endCall` döndürür. Bir geri çağırma çağrılırsa geri döndürür.  
  
 Çağrılan etkinliğin ne zaman sona erer `beginCall` döndürür, `endCall` döndürür, veya geri döndüğünde, etkinlikten çağrıldı.  
  
### <a name="asynchronous-client-without-callback"></a>Zaman uyumsuz istemci geri çağırma olmadan  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a>Her iki HTTP kullanarak yüzüne yayma etkin  
 ![Zaman uyumsuz istemci için propagateActivity ayarlandığı hiçbir geri araması ile her iki tarafında true.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-no-callback.gif)   
  
 Varsa `propagateActivity=true`, ProcessMessage aktarmak için hangi ProcessAction etkinliğini gösterir.  
  
 HTTP tabanlı senaryoları için göndermek için ilk iletiyi ReceiveBytes çağrılır ve istek ömrü boyunca mevcut.  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a>Yayma ya da HTTP kullanarak yüzüne, devre dışı bırakıldı  
 Varsa `propagateActivity=false` iki tarafında aktarmak için hangi ProcessAction etkinlik ProcessMessage göstermez. Bu nedenle, yeni bir Kimliğe sahip yeni bir geçici ProcessAction etkinlik çağrılır. ServiceModel kod isteğine zaman uyumsuz yanıt eşleştiğinde, etkinlik kimliği yerel bağlamdan alınabilir. Gerçek ProcessAction etkinlik için bu kimliğe sahip aktarılabilir  
  
 ![Zaman uyumsuz istemci ile propagateActivity taraflardan üzerinde false olarak ayarlandığı hiçbir geri çağırma.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-either-side.gif)  
    
 HTTP tabanlı senaryoları için göndermek için ilk iletiyi ReceiveBytes çağrılır ve istek ömrü boyunca mevcut.  
  
 Zaman uyumsuz bir istemcide bir işlem eylem etkinliği oluşturulur, `propagateActivity=false` çağıran ve çağrılan ve yanıt iletisi, bir eylem üst bilgisi içermez.  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a>Yayma hem TCP veya adlandırılmış kanal kullanarak yüzüne etkin  
 ![Hiçbir geri çağırma propagateActivity her iki tarafında true ve adlandırılmış ayarlandığı zaman uyumsuz istemcisiyle kanal/TCP.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-enabled-using-tcp.gif)  
  
 İstemci açılır ve bağlantı ömrü boyunca mevcut olduğunda ReceiveBytes Named-Pipe veya TCP tabanlı senaryo için çağrılır.  
  
 İlk görüntüye benzer varsa `propagateActivity=true`, ProcessMessage aktarmak için hangi ProcessAction etkinliğini gösterir.  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a>Yayma ya da TCP veya adlandırılmış kanal kullanarak yüzüne, devre dışı bırakıldı  
 İstemci açılır ve bağlantı ömrü boyunca mevcut olduğunda ReceiveBytes Named-Pipe veya TCP tabanlı senaryo için çağrılır.  
  
 Benzer şekilde, ikinci görüntü, `propagateActivity=false` iki tarafında aktarmak için hangi ProcessAction etkinlik ProcessMessage göstermez. Bu nedenle, yeni bir Kimliğe sahip yeni bir geçici ProcessAction etkinlik çağrılır. ServiceModel kod isteğine zaman uyumsuz yanıt eşleştiğinde, etkinlik kimliği yerel bağlamdan alınabilir. Gerçek ProcessAction etkinlik için bu kimliğe sahip aktarılabilir  
  
 ![Zaman uyumsuz istemci ile burada propagateActivity iki tarafındaki false olarak ayarlayın ve kanal/TCP adlı hiçbir geri çağırma.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-using-tcp.gif)  
    
### <a name="asynchronous-client-with-callback"></a>Zaman uyumsuz geri çağırma istemcisiyle  
 Bu senaryo etkinlikleri G ve A ekler ', ' geri ve `endCall`ve bunların aktarımları daraltma veya genişletme.  
  
 Bu bölüm, yalnızca HTTP kullanarak gösterir `propagateActivity` = `true`. Ancak ek etkinlikler ve aktarımları da diğer durumlarda geçerlidir (yani `propagateActivity` = `false`, TCP veya Named-Pipe kullanan).  
  
 İstemci sonuç hazır olduğunu bildiren, kullanıcı kodu çağırdığında, yeni bir etkinlik (G) geri çağırma oluşturur. Ardından kullanıcı kodu çağıran `endCall` (Şekil 5'te gösterildiği gibi) geri çağırma içinde veya dışında (Şekil 6) geri çağırma. Hangi kullanıcı etkinliğini bilinmediğinden `endCall` çağrıldığından, bu etkinlik etiketli `A’`. Mümkünse, bir ' aynı veya farklı A. olabilir  
  
 ![Zaman uyumsuz bir geri çağırma, geri çağırma içinde endcall istemcisiyle gösterir.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-in-callback.gif)  
    
 ![Zaman uyumsuz bir geri çağırma, geri çağırma dışında endcall istemcisiyle gösterir.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-outside-callback.gif)  
    
### <a name="asynchronous-server-with-callback"></a>Zaman uyumsuz geri çağırma sunucusuyla  
 ![Zaman uyumsuz bir geri çağırma sunucusuyla gösterir.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-server-callback.gif)  
    
 İstemci geri çağırır iletisi üzerinde kanal yığın: Bu işlem için izlemeler ProcessRequest etkinlik kendisini yayılan.  
  
## <a name="asynchronous-requestreply-with-errors"></a>Hatalar ile zaman uyumsuz istek/yanıt  
 Sırasında alınan hata iletisi hataları `endCall`. Aksi takdirde, etkinlikleri ve aktarımları önceki senaryolara benzer.  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a>Zaman uyumsuz olan veya olmayan hataları tek yönlü  
 İstemciye yanıt ya da hata döndürülür.
