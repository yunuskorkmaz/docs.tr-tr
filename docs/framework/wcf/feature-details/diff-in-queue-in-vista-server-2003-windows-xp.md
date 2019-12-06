---
title: Windows Vista, Windows Server 2003 ve Windows XP'de Kuyruğa Alma Özelliği Arasındaki Farklar
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF], differences in operating systems
ms.assetid: aa809d93-d0a3-4ae6-a726-d015cca37c04
ms.openlocfilehash: 77491981bdef7d02da6894cbbee93c779972d803
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837434"
---
# <a name="differences-in-queuing-features-in-windows-vista-windows-server-2003-and-windows-xp"></a>Windows Vista, Windows Server 2003 ve Windows XP'de Kuyruğa Alma Özelliği Arasındaki Farklar
Bu konu, Windows Vista, [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)]arasındaki Windows Communication Foundation (WCF) kuyrukları özelliğindeki farklılıkları özetler.  
  
## <a name="application-specific-dead-letter-queue"></a>Uygulamaya özgü atılacak mektup kuyruğu  
 Alıcı uygulama bunları zamanında okuyacaksa, sıradaki iletiler süresiz olarak kuyrukta kalabilir. İletiler zamana duyarlı ise bu davranış önerilmez. Zamana duyarlı iletilerde sıraya alınmış bağlamada ayarlanmış bir `TimeToLive` özelliği vardır. Bu özellik, iletilerin süreleri dolmadan önce kuyrukta ne kadar süreyle kalabileceğini gösterir. Süre dolmayan iletiler, teslim edilemeyen ileti sırası adlı özel bir kuyruğa gönderilir. Bir ileti ayrıca, bir kuyruk kotasının aşılması veya bir kimlik doğrulama hatası yaşaması gibi diğer nedenlerden dolayı atılacak bir sıraya göre de sona çıkabilir.  
  
 Genellikle, bir kuyruk yöneticisini paylaşan tüm sıraya alınmış uygulamalar için sistem genelinde tek bir atılacak ileti sırası vardır. Her uygulama için atılacak bir sıra, bu uygulamaların uygulamaya özel atılacak ileti kuyruğunu belirtmesini sağlayarak bir kuyruk yöneticisini paylaşan sıraya alınmış uygulamalar arasında daha iyi yalıtımı sağlar. Diğer uygulamalarla teslim edilemeyen bir ileti sırasını paylaşan bir uygulamanın, kendisine uygulanabilen iletileri bulmak için kuyruğa gözatmaları vardır. Uygulamaya özel bir atılacak ileti kuyruğu ile uygulama, atılacak ileti sırasındaki tüm iletilerin uygulanabilir olduğundan emin olabilir.  
  
 Windows Vista uygulamaya özel atılacak ileti sıraları sağlar. Uygulamaya özel atılacak ileti sıraları [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)]' de kullanılamaz ve uygulamalar sistem genelinde atılacak ileti sırasını kullanmalıdır.  
  
## <a name="poison-message-handling"></a>Zehirli Ileti Işleme  
 Zararlı bir ileti, alıcı uygulamaya yönelik en fazla teslim deneme sayısını aşmış bir iletidir. Bu durum, bir işlem sırasından ileti okuyan bir uygulama, hata nedeniyle iletiyi hemen işleyemediği zaman ortaya çıkabilir. Uygulama, sıraya alınan iletinin alındığı işlemi iptal ettiğinde, iletiyi kuyruğa döndürür. Uygulama daha sonra iletiyi yeni bir işlemde yeniden almaya çalışır. Hataya neden olan Sorun düzeltilmemişse, alıcı uygulama, en fazla teslim girişimi sayısını ve bir zarar iletisi sonucunu aşana kadar aynı iletiyi alıp iptal eden bir döngüde yer alabilir.  
  
 Windows Vista, [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)] ile ilgili Message Queuing (MSMQ) arasındaki temel farklılıklar, zarar işleme ile ilgilidir. şunları içerir:  
  
- Windows Vista 'da MSMQ alt sıraları destekler, [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)] alt sıraları desteklemez. Alt sıralar, zehirli ileti işlemede kullanılır. Yeniden deneme kuyrukları ve zarar sırası, zarar iletisi işleme ayarlarına göre oluşturulan uygulama kuyruğu için alt çizglardır. `MaxRetryCycles`, kaç yeniden deneme alt için oluşturulacağını belirler. Bu nedenle, [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] veya [!INCLUDE[wxp](../../../../includes/wxp-md.md)]çalışırken `MaxRetryCycles` yok sayılır ve `ReceiveErrorHandling.Move` izin verilmez.  
  
- Windows Vista 'da MSMQ negatif bildirimi destekler, [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)] değildir. Alma kuyruğu yöneticisinin olumsuz bir bildirimi, gönderme kuyruğu yöneticisinin reddedilen iletiyi atılacak ileti kuyruğuna yerleştirmesini sağlar. Bu nedenle, [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)]`ReceiveErrorHandling.Reject` izin verilmez.  
  
- Windows Vista 'da MSMQ, ileti tesliminin denenme sayısı sayısını tutan bir ileti özelliğini destekler. Bu Abort Count özelliği [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)]üzerinde kullanılamaz. WCF, iptal sayısını bellekte tutar, bu nedenle aynı ileti bir Web grubunda birden fazla WCF hizmeti tarafından okunabildiği zaman bu özelliğin doğru bir değer içermemesi olasıdır.  
  
## <a name="remote-transactional-read"></a>Uzaktan Işlem okuma  
 Windows Vista 'da MSMQ, uzaktan işlem okumaları destekler. Bu, bir kuyruktan okuyan bir uygulamanın, sıranın barındırıldığı bilgisayardan farklı bir bilgisayarda barındırılmasına olanak sağlar. Bu, sistemin genel verimini artıran merkezi bir kuyruktan okuma hizmetleri grubuna sahip olmanızı sağlar. Ayrıca iletiyi okurken ve işlerken bir hata oluşursa, işlem geri kaydedilir ve ileti daha sonra işlenmek üzere kuyrukta kalır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İleti Aktarımı Hatalarını İşlemek için Teslim Edilemeyen İletiler Sırası Kullanma](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)
- [Zehirli İleti İşleme](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)
