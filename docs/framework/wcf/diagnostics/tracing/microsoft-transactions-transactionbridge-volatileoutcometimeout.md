---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.date: 03/30/2017
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
ms.openlocfilehash: b64f61d25c3be87019151cbf560becd3384ec182
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33475637"
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a>Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
WS-AT protokolü hizmetini geçici katılımcı sonucu iletisine yanıt beklerken zaman aşımına uğradı. Katılımcı döndürürse, işlem sonucu şüpheli olabilir.  
  
## <a name="description"></a>Açıklama  
 İzlenen Volatile katılımcı tamamlama veya iptal etmeye karar ancak belirli bir süre içinde bir yürütme veya geri alma isteğine yanıt vermedi.  
  
## <a name="troubleshooting"></a>Sorun giderme  
 Tüm Volatile katılımcılar verilen sürede yanıt verebilmesini olduğundan emin olun. Varsayılan süre 180 saniyedir.  Bu yetersiz ise artırmak `VolatileOutcomeDelay` WS-AT için Zamanlayıcı ilkesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Uygulamanızda Sorun Giderme için İzleme Kullanma](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Yönetim ve Tanılama](../../../../../docs/framework/wcf/diagnostics/index.md)
