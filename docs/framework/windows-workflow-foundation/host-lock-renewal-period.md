---
title: Konak Kilidi Yenileme Dönemi
ms.date: 03/30/2017
ms.assetid: f8ba94fc-27e0-4d8e-8f85-50a6d2a3cd43
ms.openlocfilehash: 82073377353be6d4f8a7d0a343c31f2b49a2873f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268202"
---
# <a name="host-lock-renewal-period"></a>Konak Kilidi Yenileme Dönemi

SQL Iş akışı örneği deposunun **konak kilit yenileme süresi** özelliği, konağın bir iş akışı örneği üzerinde kilidini yenilediğini belirten süreyi belirtmenize olanak tanır. Kilit, ana bilgisayar kilidi yenileme süresi + 30 saniye için geçerli kalır. Ana bilgisayar kilidi yenilemezse (diğer bir deyişle, kirayı bu zaman aralığında uzatırsa), kilidin süresi dolar ve kalıcılık sağlayıcısı örneğin kilidini açar. Bu özelliğin değeri "hh: mm: ss" biçiminde TimeSpan türündedir. İzin verilen en düşük değer "00:00:01" değeridir (1 saniye). Bu özelliğin varsayılan değeri "00:00:30" (30 saniye) değeridir.  
  
 Bu özellik, bir iş akışı hizmeti konağının, sahip olduğu bir iş akışı hizmeti örneğinin kilidini açmasından önce başarısız olduğu senaryolarda önemli bir özelliktir. Bu senaryoda, aynı bilgisayar üzerinde çalışan başka bir iş akışı hizmeti konağının veya bir sunucu grubundaki başka bir bilgisayar kilidi alabilir ve iş akışı hizmet örneğini en son kalıcı durumundan devam ettirmeye devam etmek için belleğe yükleyebilir, bu durumda, kalıcılık veritabanındaki iş akışı hizmeti örneğindeki kilit, kilitlenme sağlayıcısı tarafından kaldırılır.  
  
 Bu özellik için daha yüksek bir değer ayarlandığında, iş akışı hizmeti örneklerinin Kalıcılık veritabanında daha uzun bir süre kilitlenmesine neden olur ve bu nedenle örneği son Kalıcılık noktasından kurtarmaya gecikir. Bu özellik için kısa bir Aralık ayarlamak, iş akışı hizmet ana bilgisayarının yeni örneğinin başarısız iş akışı hizmeti örneğini hızla seçmesini sağlar, ancak iş akışı hizmeti ana bilgisayarı ve SQL Server veritabanı için iş yükünde artışa neden olur.  
  
 SQL Iş akışı örneği deposu, düzenli aralıklarla uyandığı iç bir görev çalıştırır ve bunlar üzerinde zaman aşımına uğradı. Süre dolma kilitleri olan örnekleri bulduğunda, örnekleri Runnableınstances tablosuna koyar, böylece iş akışı ana bilgisayarı bu örnekleri alabilir ve çalıştırabilir.
