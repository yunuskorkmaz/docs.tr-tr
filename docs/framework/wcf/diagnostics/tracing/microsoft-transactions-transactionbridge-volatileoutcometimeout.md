---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.date: 03/30/2017
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
ms.openlocfilehash: fac3682a955ed0caf21fdb1dea48672bf3bdea77
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704582"
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a>Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
WS-AT protokolü hizmetini geçici bir katılımcı sonucu iletisine yanıt beklerken zaman aşımına uğradı. Katılımcı döndürürse, şüpheli işlem sonucu olabilir.  
  
## <a name="description"></a>Açıklama  
 Geçici bir katılımcı tamamlama veya iptal karar verdi, ancak bir yürütme veya geri alma isteği için belirli bir süre içinde yanıt vermedi izlenen.  
  
## <a name="troubleshooting"></a>Sorun giderme  
 Tüm geçici katılımcıları belirtilen süre içinde yanıt verebilir durumda olduğundan emin olun. Varsayılan süre 180 saniyedir.  Bu yetersiz kalırsa, artırmak `VolatileOutcomeDelay` WS-AT Zamanlayıcı ilkesini.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Uygulamanızda Sorun Giderme için İzleme Kullanma](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Yönetim ve Tanılama](../../../../../docs/framework/wcf/diagnostics/index.md)
