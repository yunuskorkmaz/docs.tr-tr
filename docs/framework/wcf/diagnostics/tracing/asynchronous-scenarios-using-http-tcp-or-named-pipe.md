---
title: HTTP, TCP veya Named-Pipe Kullanan Zaman Uyumsuz Senaryolar
ms.date: 03/30/2017
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
ms.openlocfilehash: d08f70186a59b8717c4441167ee720ba1c20b9dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998296"
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a>HTTP, TCP veya Named-Pipe Kullanan Zaman Uyumsuz Senaryolar
Bu konuda etkinlikler ve aktarımları farklı zaman uyumsuz istek/yanıt senaryoları için TCP ve HTTP kullanarak birden çok iş parçacıklı isteklerle açıklar veya adlandırılmış.  
  
## <a name="asynchronous-requestreply-without-errors"></a>Zaman uyumsuz istek/yanıt hatasız  
 Bu bölümde, etkinlikleri ve aktarımlar için birden çok iş parçacıklı istemcilerle bir zaman uyumsuz istek/yanıt senaryosu açıklanmaktadır.  
  
 Arayan etkinlik ne zaman sona erer `beginCall` döndürür, ve `endCall` döndürür. Bir geri çağırma çağrılırsa geri döndürür.  
  
 Çağrılan etkinliğin ne zaman sona erer `beginCall` döndürür, `endCall` döndürür, veya geri döndüğünde, etkinlikten çağrıldı.  
  
### <a name="asynchronous-client-without-callback"></a>Zaman uyumsuz istemci geri çağırma olmadan  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a>Her iki HTTP kullanarak yüzüne yayma etkin  
 ![Zaman uyumsuz senaryolar](../../../../../docs/framework/wcf/diagnostics/tracing/media/asyn1.gif "Asyn1")  
  
 Şekil 1. Zaman uyumsuz istemci, hiçbir geri çağırma `propagateActivity` = `true` her iki tarafında, HTTP  
  
 Varsa `propagateActivity` = `true`, ProcessMessage aktarmak için hangi ProcessAction etkinliğini gösterir.  
  
 HTTP tabanlı senaryoları için göndermek için ilk iletiyi ReceiveBytes çağrılır ve istek ömrü boyunca mevcut.  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a>Yayma ya da HTTP kullanarak yüzüne, devre dışı bırakıldı  
 Varsa `propagateActivity` = `false` iki tarafında aktarmak için hangi ProcessAction etkinlik ProcessMessage göstermez. Bu nedenle, yeni bir Kimliğe sahip yeni bir geçici ProcessAction etkinlik çağrılır. ServiceModel kod isteğine zaman uyumsuz yanıt eşleştiğinde, etkinlik kimliği yerel bağlamdan alınabilir. Gerçek ProcessAction etkinlik için bu kimliğe sahip aktarılabilir  
  
 ![HTTP kullanan zaman uyumsuz senaryolar&#47;TCP&#47;adlandırılmış kanal](../../../../../docs/framework/wcf/diagnostics/tracing/media/async2.gif "Async2")  
  
 Şekil 2. Zaman uyumsuz istemci, hiçbir geri çağırma `propagateActivity` = `false` iki tarafındaki HTTP  
  
 HTTP tabanlı senaryoları için göndermek için ilk iletiyi ReceiveBytes çağrılır ve istek ömrü boyunca mevcut.  
  
 Zaman uyumsuz bir istemcide bir işlem eylem etkinliği oluşturulur, `propagateActivity` = `false` çağıran ve çağrılan ve yanıt iletisi, bir eylem üst bilgisi içermez.  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a>Yayma hem TCP veya adlandırılmış kanal kullanarak yüzüne etkin  
 ![HTTP kullanan zaman uyumsuz senaryolar&#47;TCP&#47;adlandırılmış kanal](../../../../../docs/framework/wcf/diagnostics/tracing/media/async3.gif "Async3")  
  
 Şekil 3. Zaman uyumsuz istemci, hiçbir geri çağırma `propagateActivity` = `true` her iki tarafında Named-Pipe/TCP  
  
 İstemci açılır ve bağlantı ömrü boyunca mevcut olduğunda ReceiveBytes Named-Pipe veya TCP tabanlı senaryo için çağrılır.  
  
 Benzer şekilde, Şekil 1, `propagateActivity` = `true`, ProcessMessage aktarmak için hangi ProcessAction etkinliğini gösterir.  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a>Yayma ya da TCP veya adlandırılmış kanal kullanarak yüzüne, devre dışı bırakıldı  
 İstemci açılır ve bağlantı ömrü boyunca mevcut olduğunda ReceiveBytes Named-Pipe veya TCP tabanlı senaryo için çağrılır.  
  
 Benzer şekilde, Fig.2 varsa `propagateActivity` = `false` iki tarafında aktarmak için hangi ProcessAction etkinlik ProcessMessage göstermez. Bu nedenle, yeni bir Kimliğe sahip yeni bir geçici ProcessAction etkinlik çağrılır. ServiceModel kod isteğine zaman uyumsuz yanıt eşleştiğinde, etkinlik kimliği yerel bağlamdan alınabilir. Gerçek ProcessAction etkinlik için bu kimliğe sahip aktarılabilir  
  
 ![HTTP kullanan zaman uyumsuz senaryolar&#47;TCP&#47; adlandırılmış kanallar](../../../../../docs/framework/wcf/diagnostics/tracing/media/async4.gif "Async4")  
  
 Şekil 4 '. Zaman uyumsuz istemci, hiçbir geri çağırma `propagateActivity` = `false` iki tarafındaki Named-Pipe/TCP  
  
### <a name="asynchronous-client-with-callback"></a>Zaman uyumsuz geri çağırma istemcisiyle  
 Bu senaryo etkinlikleri G ve A ekler ', ' geri ve `endCall`ve bunların aktarımları daraltma veya genişletme.  
  
 Bu bölüm, yalnızca HTTP kullanarak gösterir `propragateActivity` = `true`. Ancak ek etkinlikler ve aktarımları da diğer durumlarda geçerlidir (yani `propagateActivity` = `false`, TCP veya Named-Pipe kullanan).  
  
 İstemci sonuç hazır olduğunu bildiren, kullanıcı kodu çağırdığında, yeni bir etkinlik (G) geri çağırma oluşturur. Ardından kullanıcı kodu çağıran `endCall` (Şekil 5'te gösterildiği gibi) geri çağırma içinde veya dışında (Şekil 6) geri çağırma. Hangi kullanıcı etkinliğini bilinmediğinden `endCall` çağrıldığından, bu etkinlik etiketli `A’`. Mümkünse, bir ' aynı veya farklı A. olabilir  
  
 ![Zaman uyumsuz senaryolar](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback1.gif "AsyncCallback1")  
  
 Şekil 5 '. Zaman uyumsuz geri çağırma, istemci `endCall` içinde geri çağırma  
  
 ![Zaman uyumsuz senaryolar](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback2.gif "AsyncCallback2")  
  
 Şekil 6. Zaman uyumsuz geri çağırma, istemci `endCall` dışında geri çağırma  
  
### <a name="asynchronous-server-with-callback"></a>Zaman uyumsuz geri çağırma sunucusuyla  
 ![HTTP kullanan zaman uyumsuz senaryolar&#47;TCP&#47; adlandırılmış&#45;kanal](../../../../../docs/framework/wcf/diagnostics/tracing/media/aynchserver.gif "AynchServer")  
  
 Şekil 7. Zaman uyumsuz sunucu geri çağırma  
  
 İstemci geri çağırır iletisi üzerinde kanal yığın: Bu işlem için izlemeler ProcessRequest etkinlik kendisini yayılan.  
  
## <a name="asynchronous-requestreply-with-errors"></a>Hatalar ile zaman uyumsuz istek/yanıt  
 Sırasında alınan hata iletisi hataları `endCall`. Aksi takdirde, etkinlikleri ve aktarımları önceki senaryolara benzer.  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a>Zaman uyumsuz olan veya olmayan hataları tek yönlü  
 İstemciye yanıt ya da hata döndürülür.
