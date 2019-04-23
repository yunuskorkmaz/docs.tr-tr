---
title: Windows Vista, Windows Server 2003 ve Windows XP'de Kuyruğa Alma Özelliği Arasındaki Farklar
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF], differences in operating systems
ms.assetid: aa809d93-d0a3-4ae6-a726-d015cca37c04
ms.openlocfilehash: d13cb3e732d0276902def5de6ca7c007f61b0ec9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115992"
---
# <a name="differences-in-queuing-features-in-windows-vista-windows-server-2003-and-windows-xp"></a>Windows Vista, Windows Server 2003 ve Windows XP'de Kuyruğa Alma Özelliği Arasındaki Farklar
Bu konuda, Windows Communication Foundation (WCF) kuyrukları özelliği farklar özetlenmektedir [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
## <a name="application-specific-dead-letter-queue"></a>Uygulamaya özgü eski ileti sırası  
 Alıcı uygulama bunları vakitli şekilde okumaz, kuyruğa alınmış iletiler kuyrukta süresiz olarak kalır. Bu davranış, iletileri zamana duyarlı olması durumunda önerilmez. Zamana duyarlı iletileriniz bir `TimeToLive` sıraya alınan bağlamasında özelliği. Bu özellik, süresi dolmadan önce ne kadar süreyle iletiler kuyrukta olabilir gösterir. Süresi dolan iletileri eski ileti sırası adı verilen özel bir kuyruğa gönderilir. Bir ileti ayrıca bir kuyruk kotasını veya bir kimlik doğrulama hatasının oluştuğu gibi başka nedenlerle edilemeyen kuyrukta kalabilirsiniz.  
  
 Genellikle, bir kuyruk Yöneticisi paylaşan tüm kuyruğa alınan uygulamalar için tek bir sistem genelinde eski ileti sırası mevcut. Atılacak her uygulama için bir kuyruk Yöneticisi kendi uygulamaya özgü sahipsiz sırayı belirtmek bu uygulamaların vererek paylaşan kuyruğa alınmış uygulamalar arasında daha iyi yalıtım sağlar. Diğer uygulamalarla eski ileti sırası paylaşan bir uygulama için geçerli olan iletileri bulmak için kuyruk göz atmak vardır. Bir uygulamaya özgü eski ileti sırası, uygulama kendi edilemeyen kuyruğundaki tüm iletileri için geçerli olduğundan emin olabilirsiniz.  
  
 [!INCLUDE[wv](../../../../includes/wv-md.md)] uygulamaya özgü edilemeyen için sağlar. Uygulamaya özgü edilemeyen kullanılabilir olmayan [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)], ve uygulamaları, sistem genelinde eski ileti sırası kullanması gerekir.  
  
## <a name="poison-message-handling"></a>Poison ileti işleme  
 Zehirli ileti alıcı uygulamasına teslim denemesi üst sınırını aşan bir iletidir. İşlem kuyruktan bir ileti yazan bir uygulama iletisi hemen hataları nedeniyle işleyemiyor olduğunda bu durum ortaya çıkabilir. Kuyruğa Alınan iletinin alındığı işlem uygulamayı durdurur, kuyruğa bir ileti döndürür. Uygulama, yeni bir işlemde iletisi almayı dener. Hataya neden olan sorun düzeltilmezse alıcı uygulama alma ve aynı iletiyi teslim denemesi üst sınırını aşıyor ve zehirli ileti sonuçları kadar durduruluyor bir döngüde takılı.  
  
 Temel farklılıklar arasında Message Queuing (MSMQ) üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)] zehirli işleme için uygun olan şunları içerir:  
  
-   MSMQ [!INCLUDE[wv](../../../../includes/wv-md.md)] sıralar, destekler ancak [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)] sıralar desteklemez. Poison ileti işlemede kullanılan sıralar. Yeniden deneme kuyrukları ve zehirli kuyruk zarar ileti işleme ayarlara göre oluşturulan uygulama kuyruğa sıralar var. `MaxRetryCycles` Kaç yeniden oluşturmak için sıralar belirler. Bu nedenle, çalışırken [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] veya [!INCLUDE[wxp](../../../../includes/wxp-md.md)], `MaxRetryCycles` göz ardı edilir ve `ReceiveErrorHandling.Move` izin verilmiyor.  
  
-   MSMQ [!INCLUDE[wv](../../../../includes/wv-md.md)] destekler bildirimi, negatif sırada [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)] değildir. Alıcı sırası Yöneticisi'nden negatif bildirim edilemeyen kuyrukta reddedilen ileti yerleştirmek gönderme sıra yöneticisini neden olur. Bu nedenle, `ReceiveErrorHandling.Reject` ile izin verilmiyor [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
-   MSMQ [!INCLUDE[wv](../../../../includes/wv-md.md)] ileti teslimi sürelerini sayısını tutan bir ileti özelliği denenir destekler. Bu durdurma sayısı özelliği kullanılabilir değil [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)]. Onu aynı message Web çiftliğindeki birden WCF servis okunduğunda buözellik doğru bir değer içeremeyeceğini mümkündür WCF abort count bellekteyse tutar.  
  
## <a name="remote-transactional-read"></a>Uzak işlem okuma  
 MSMQ üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)] uzak işlem okuma destekler. Bu sıranın barındıran bilgisayardan farklı bir bilgisayar üzerinde barındırılması için bir kuyruktan okuyan bir uygulama sağlar. Bu, sistemin genel performansını artıran bir merkezi kuyruktan okuma Hizmetleri grubu kabiliyeti sağlar. Ayrıca, okuma ve iletiyi işlerken bir hata oluşması, geri işlem yapar ve daha sonra işlenmek sırasındaki ileti kalır sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İleti Aktarımı Hatalarını İşlemek için Teslim Edilemeyen İletiler Sırası Kullanma](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)
- [Zehirli İleti İşleme](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)
