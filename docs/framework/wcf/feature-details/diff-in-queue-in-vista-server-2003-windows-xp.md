---
title: "Windows Vista, Windows Server 2003 ve Windows XP'de Kuyruğa Alma Özelliği Arasındaki Farklar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: queues [WCF], differences in operating systems
ms.assetid: aa809d93-d0a3-4ae6-a726-d015cca37c04
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 669c6be6756d79b30266c9fda0909fedc71aeae3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="differences-in-queuing-features-in-windows-vista-windows-server-2003-and-windows-xp"></a>Windows Vista, Windows Server 2003 ve Windows XP'de Kuyruğa Alma Özelliği Arasındaki Farklar
Bu konu farkları özetler [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sıraları özellik arasında [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
## <a name="application-specific-dead-letter-queue"></a>Uygulamaya özgü eski ileti sırası  
 Alma işlemini yapan uygulamanın bunları zamanında okumaz, sıraya alınan iletileri kuyruğa süresiz olarak kalabilir. Bu davranış, iletileri zamana duyarlı olup olmadığını önerilmez. Zamana duyarlı iletileri sahip bir `TimeToLive` özelliği sıraya alınan bağlamasında ayarlanmış. Bu özellik, süresi dolmadan önce ne kadar süreyle iletiler kuyrukta olabilir gösterir. Süresi dolan iletileri sahipsiz sıra adı verilen bir özel sıra için gönderilir. Bir ileti ayrıca bir sıra kotasını veya bir kimlik doğrulama hatasının oluştuğu gibi diğer nedenlerle bir sahipsiz sıraya düşebilir.  
  
 Genellikle, tek bir sistem genelinde sahipsiz sıraya sıra yöneticisi paylaşan tüm kuyruğa alınan uygulamalarının bulunmaktadır. Sahipsiz sıra her uygulama için bir sıra yöneticisi kendi uygulamaya özgü sahipsiz sırayı belirtmek bu uygulamaları izin vererek paylaşmak sıraya alınan uygulamalar arasında daha iyi yalıtım sağlar. Diğer uygulamalarla sahipsiz sırayı paylaşan bir uygulama için geçerli olan iletileri bulmak için sıra göz atmak sahiptir. Bir uygulamaya özgü sahipsiz sırayı uygulamanın kendi sahipsiz sıradaki tüm iletileri için geçerli olduğundan emin olabilirsiniz.  
  
 [!INCLUDE[wv](../../../../includes/wv-md.md)]uygulamaya özgü sıralarındaki için sağlar. Uygulamaya özgü sıralarındaki kullanılabilir olmayan [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)], ve uygulamaları, sistem genelinde sahipsiz sırayı kullanmalıdır.  
  
## <a name="poison-message-handling"></a>Poison ileti işleme  
 Zararlı bir ileti teslim alma işlemini yapan uygulamanın girişimleri üst sınırını aştı bir iletidir. İşlem bir sıradan ileti okuyan bir uygulama iletiyi hemen hatalar nedeniyle işleyemediğinde bu durum ortaya çıkabilir. Kuyruğa Alınan iletinin alındığı işlem uygulama durdurur, kuyruğa ileti döndürür. Uygulama, yeni bir işlemde ileti almayı dener. Hataya neden olan sorun düzeltilmezse alma işlemini yapan uygulamanın alma ve teslim girişimleri üst sınırını aşıyor ve zararlı bir ileti sonuçları kadar aynı iletiyi durduruluyor bir döngüye.  
  
 Temel farklılıklar arasında Message Queuing (MSMQ) üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)] zararlı işleme ilgili olan şunları içerir:  
  
-   MSMQ [!INCLUDE[wv](../../../../includes/wv-md.md)] sıralar, destekler ancak [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)] sıralar desteklemez. Alt sıralar poison-ileti işleme kullanılır. Yeniden deneme sıralarındaki ve zararlı sıranın poison ileti işleme ayarlara göre oluşturulan uygulama sırasındaki sıralara markalarıdır. `MaxRetryCycles` Kaç tane oluşturmak için sıralar yeniden deneme belirler. Bu nedenle, çalışırken [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] veya [!INCLUDE[wxp](../../../../includes/wxp-md.md)], `MaxRetryCycles` göz ardı edilir ve `ReceiveErrorHandling.Move` verilmez.  
  
-   MSMQ [!INCLUDE[wv](../../../../includes/wv-md.md)] destekler negatif bildirim, sırada [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)] desteklemez. Olumsuz bildirim alma sıra Yöneticisi'nden sahipsiz sıraya reddedilen ileti yerleştirmek gönderme sıra Yöneticisi neden olur. Bu nedenle, `ReceiveErrorHandling.Reject` ile izin verilmiyor [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
-   MSMQ [!INCLUDE[wv](../../../../includes/wv-md.md)] ileti teslimi kaç kez sayısını tutar bir ileti özelliği denemesi destekler. Bu iptal sayısı özelliği kullanılabilir değil [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)]. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]aynı iletiyi birden fazla tarafından okunduğunda bu özelliği doğru bir değer içeremez mümkün olacak şekilde durdurma sayısı bellekte saklar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bir Web grubu hizmeti.  
  
## <a name="remote-transactional-read"></a>Uzak işlem okuma  
 MSMQ üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)] uzak işlem okuma destekler. Bu sıranın barındırılan bilgisayardan farklı bir bilgisayar üzerinde barındırılması için bir sıra okunurken bir uygulama sağlar. Bu sistemin genel üretilen işi artıran bir merkezi sıradan okuma hizmetlerinin bir gruba sahip olma yeteneği sağlar. Ayrıca, okuma ve ileti işlenirken bir hata oluşur, işlem geri alınır ve daha sonra işlenmek sırasındaki ileti kalır sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İleti aktarımı hatalarını işlemek için teslim edilemeyen iletiler sırası kullanma](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 [Zehirli ileti işleme](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)
