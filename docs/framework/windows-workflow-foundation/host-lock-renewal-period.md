---
title: Konak Kilidi Yenileme Dönemi
ms.date: 03/30/2017
ms.assetid: f8ba94fc-27e0-4d8e-8f85-50a6d2a3cd43
ms.openlocfilehash: 91d83259c766120f7e3ffc9e49f1cf1b18c32a18
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945619"
---
# <a name="host-lock-renewal-period"></a>Konak Kilidi Yenileme Dönemi
**Konak kilidi yenileme dönemi** SQL iş akışı örneği Store özelliğini konak içinde bir iş akışı örneği kilidini yeniler zaman aralığı belirtmenize olanak sağlar. Kilit geçerli kaldığı için konak kilidi yenileme dönemi + 30 saniye. Konak kilidi yenileme başarısız olursa (diğer bir deyişle, kiralama genişletme) bu süre içinde kilidi süresi dolar ve kalıcı bir sağlayıcı örneği kilidini açar. The value for this property is of type TimeSpan of the form "hh:mm:ss". Değer izin verilen minimum "00: 00:01" (1 saniye). Bu özelliğin varsayılan değeri "00: 00:30" (30 saniye).  
  
 Bu özellik, sahibi bir iş akışı hizmet örneği kilidini açmak önce bir iş akışı hizmeti konağı burada başarısız senaryolarda önemlidir. Bu senaryoda aynı bilgisayara veya bir sunucu grubundaki başka bir bilgisayar üzerinde çalışan başka bir iş akışı hizmeti konağı elde edebilir, böylece kilidin süresi dolduktan sonra kalıcı bir sağlayıcı tarafından Kalıcılık veritabanı'nda iş akışı hizmet örneği üzerindeki kilit kaldırılır Kilit ve iş akışı hizmet örneği, sürdürebilir, son kalıcı durumdan belleğe yüklemek.  
  
 Bu özellik için daha yüksek bir değere ayarlamak, iş akışı hizmet örnekleri daha uzun bir süre içinde Kalıcılık veritabanı kilitlenmesine neden olur ve bu nedenle örneğinin son Kalıcılık noktasından kurtarma geciktirir. Bu özellik için kısa bir süre ayarlama başarısız iş akışı hizmeti örneği hızlı bir şekilde seçmek için iş akışı hizmeti ana bilgisayarı yeni bir örneğini neden olur, ancak iş akışı hizmeti ana bilgisayarı ve SQL Server veritabanı için iş yükünde artışa neden olur.  
  
 SQL iş akışı örneği Store düzenli aralıklarla uyanır ve bunları süresi dolmuş kilitler örnekleriyle algılar bir iç görev çalıştırır. Süresi dolan kilitleri örnekleriyle bulur, böylece bir iş akışı ana bilgisayarı almak ve Bu örneklerin RunnableInstances tabloda örnekleri yerleştirir.
