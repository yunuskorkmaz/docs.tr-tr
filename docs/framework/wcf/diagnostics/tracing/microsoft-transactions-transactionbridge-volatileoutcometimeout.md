---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.date: 03/30/2017
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
ms.openlocfilehash: dd2a0b67ec140aa2e6fe1abad8e85c0206abd8ea
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579027"
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a>Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
WS-AT protokol hizmeti, geçici bir katılımcıdan bir sonuç iletisine yanıt beklerken zaman aşımına uğradı. Katılımcı geri dönerse, işlem sonucu şüpheli olabilir.  
  
## <a name="description"></a>Açıklama  
 Geçici katılımcı Işlemeye veya durdurmaya karar verdiğinde, ancak belirli bir süre içinde bir COMMIT veya Rollback isteğine yanıt vermediğini izlendi.  
  
## <a name="troubleshooting"></a>Sorun giderme  
 Tüm geçici katılımcıların verilen süre içinde yanıt verebilmesini sağlayın. Varsayılan zaman aralığı 180 saniyedir.  Bu yeterli değilse, `VolatileOutcomeDelay` ws-at zamanlayıcı ilkesini artırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzleme](index.md)
- [Uygulamanızda Sorun Giderme için İzleme Kullanma](using-tracing-to-troubleshoot-your-application.md)
- [Yönetim ve tanılama](../index.md)
