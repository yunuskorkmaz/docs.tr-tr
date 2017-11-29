---
title: HTTP, TCP veya Named-Pipe Kullanan Zaman Uyumsuz Senaryolar
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c697069aad590013ff360eb6ee4cba39468b89d5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a>HTTP, TCP veya Named-Pipe Kullanan Zaman Uyumsuz Senaryolar
Bu konuda veya adlandırılmış etkinlikleri ve aktarımlar farklı zaman uyumsuz istek/yanıt senaryoları için HTTP, TCP, kullanarak birden çok iş parçacıklı isteklerle açıklanır.  
  
## <a name="asynchronous-requestreply-without-errors"></a>Zaman uyumsuz istek/yanıt hatasız  
 Bu bölümde etkinlikler ve aktarımlar için birden çok iş parçacıklı istemcilerle bir zaman uyumsuz istek/yanıt senaryosu açıklanmaktadır.  
  
 Arayan etkinlik ne zaman sona erer `beginCall` döndürür, ve `endCall` döndürür. Bir geri çağırma çağrılıp çağrılmayacağını geri döndürür.  
  
 Çağrılan etkinlik ne zaman sona erer `beginCall` döndürür, `endCall` döndürür, ya da geri döndüğünde bu etkinliğinden çağrıldı durumunda.  
  
### <a name="asynchronous-client-without-callback"></a>Zaman uyumsuz istemcisi olmadan geri çağırma  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a>Her iki HTTP kullanarak tarafta yayma etkin  
 ![Zaman uyumsuz senaryolar](../../../../../docs/framework/wcf/diagnostics/tracing/media/asyn1.gif "Asyn1")  
  
 Şekil 1 '. Zaman uyumsuz istemcisi, bir geri çağırma `propagateActivity` = `true` her iki tarafında, HTTP  
  
 Varsa `propagateActivity` = `true`, ProcessMessage aktarmak için hangi ProcessAction etkinliği gösterir.  
  
 HTTP tabanlı senaryoları için ReceiveBytes göndermek için ilk ileti çağrılır ve istek ömrü boyunca bulunmaktadır.  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a>Yayma ya da HTTP kullanarak tarafta, devre dışı bırakıldı  
 Varsa `propagateActivity` = `false` iki tarafında aktarmak için hangi ProcessAction etkinlik ProcessMessage göstermez. Bu nedenle, yeni bir kimliği ile yeni bir geçici ProcessAction etkinlik çağrılır. ServiceModel kod istek için zaman uyumsuz yanıt eşleştiğinde, etkinlik kimliği yerel bağlamdan alınabilir. Gerçek ProcessAction etkinlik için bu kimliğe sahip aktarılabilir  
  
 ![HTTP &#47;kullanarak zaman uyumsuz senaryolar; TCP &#47; Adlandırılmış kanal](../../../../../docs/framework/wcf/diagnostics/tracing/media/async2.gif "Async2")  
  
 Şekil 2 '. Zaman uyumsuz istemcisi, bir geri çağırma `propagateActivity` = `false` her iki tarafında, HTTP  
  
 HTTP tabanlı senaryoları için ReceiveBytes göndermek için ilk ileti çağrılır ve istek ömrü boyunca bulunmaktadır.  
  
 Bir işlem eylem etkinlik zaman uyumsuz bir istemcide oluşturulan zaman `propagateActivity` = `false` çağıran ve çağrılan ve yanıt iletisi bir eylem üstbilgisi içermez.  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a>Yayma hem TCP veya adlandırılmış kanal kullanarak tarafta etkin  
 ![HTTP &#47;kullanarak zaman uyumsuz senaryolar; TCP &#47; Adlandırılmış kanal](../../../../../docs/framework/wcf/diagnostics/tracing/media/async3.gif "Async3")  
  
 Şekil 3 '. Zaman uyumsuz istemcisi, bir geri çağırma `propagateActivity` = `true` her iki tarafında Named-Pipe/TCP  
  
 İstemci açılmış ve bağlantı ömrü için mevcut bir adlandırılmış kanal veya TCP tabanlı senaryo için ReceiveBytes çağrılır.  
  
 Benzer ise 1, Şekil `propagateActivity` = `true`, ProcessMessage aktarmak için hangi ProcessAction etkinliği gösterir.  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a>Yayma ya da TCP veya adlandırılmış kanal kullanarak tarafta, devre dışı bırakıldı  
 İstemci açılmış ve bağlantı ömrü için mevcut bir adlandırılmış kanal veya TCP tabanlı senaryo için ReceiveBytes çağrılır.  
  
 Benzer şekilde Fig.2, varsa `propagateActivity` = `false` iki tarafında aktarmak için hangi ProcessAction etkinlik ProcessMessage göstermez. Bu nedenle, yeni bir kimliği ile yeni bir geçici ProcessAction etkinlik çağrılır. ServiceModel kod istek için zaman uyumsuz yanıt eşleştiğinde, etkinlik kimliği yerel bağlamdan alınabilir. Gerçek ProcessAction etkinlik için bu kimliğe sahip aktarılabilir  
  
 ![HTTP &#47;kullanarak zaman uyumsuz senaryolar; TCP &#47; Adlandırılmış Kanallar](../../../../../docs/framework/wcf/diagnostics/tracing/media/async4.gif "Async4")  
  
 Şekil 4 '. Zaman uyumsuz istemcisi, bir geri çağırma `propagateActivity` = `false` her iki tarafında Named-Pipe/TCP  
  
### <a name="asynchronous-client-with-callback"></a>Zaman uyumsuz istemci geri araması ile  
 Bu senaryo etkinlikleri G ve A ekler ', ' geri ve `endCall`ve bunların aktarımları giriş/çıkış.  
  
 Bu bölüm, yalnızca HTTP kullanarak gösterir `propragateActivity` = `true`. Ancak, ek etkinlikler ve aktarımları de diğer örnekleri için geçerlidir (yani, `propagateActivity` = `false`, TCP veya Named-Pipe kullanan).  
  
 İstemci sonuç hazır olduğunu bildirmek için kullanıcı kodu çağırdığında geri çağırma yeni bir etkinlik (G) oluşturur. Kullanıcı kodu daha sonra çağırır `endCall` (Şekil 5'te gösterildiği gibi) geri çağırma içinde veya dışında geri çağırma (Şekil 6). Hangi kullanıcı etkinliği bilinmediğinden `endCall` çağrıldığından, bu etkinlik etiketli `A’`. Mümkünse A' özdeş veya A. farklı olabilir  
  
 ![Zaman uyumsuz senaryolar](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback1.gif "AsyncCallback1")  
  
 Şekil 5. Zaman uyumsuz geri çağırma, istemciyle `endCall` içinde geri çağırma  
  
 ![Zaman uyumsuz senaryolar](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback2.gif "AsyncCallback2")  
  
 Şekil 6. Zaman uyumsuz geri çağırma, istemciyle `endCall` geri çağırma dışında  
  
### <a name="asynchronous-server-with-callback"></a>Zaman uyumsuz geri çağırma sunucusuyla  
 ![HTTP &#47;kullanarak zaman uyumsuz senaryolar; TCP &#47; Adlı &#45; Kanal](../../../../../docs/framework/wcf/diagnostics/tracing/media/aynchserver.gif "AynchServer")  
  
 Şekil 7. Zaman uyumsuz sunucusuyla, geri çağırma  
  
 İstemci geri çağrıları iletisi alıyorsunuz kanal yığın: Bu işlem için izlemeleri ProcessRequest etkinlik kendisini yayılan.  
  
## <a name="asynchronous-requestreply-with-errors"></a>Zaman uyumsuz istek/yanıt hatalı  
 Sırasında alınan hata iletisi hataları `endCall`. Aksi takdirde, etkinlikler ve aktarımları önceki senaryolara benzer.  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a>Zaman uyumsuz olan veya olmayan hataları tek yönlü  
 İstemciye yanıt ya da hata döndürülür.
