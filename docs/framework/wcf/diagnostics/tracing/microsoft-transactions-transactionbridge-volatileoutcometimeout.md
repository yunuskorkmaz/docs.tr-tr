---
description: 'Hakkında daha fazla bilgi edinin: Microsoft. Transactions. TransactionBridge. VolatileOutcomeTimeout'
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.date: 03/30/2017
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
ms.openlocfilehash: 5dd6ecce995d315581e1335e4dc83c425a6381b7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677242"
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a>Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout

WS-AT protokol hizmeti, geçici bir katılımcıdan bir sonuç iletisine yanıt beklerken zaman aşımına uğradı. Katılımcı geri dönerse, işlem sonucu şüpheli olabilir.  
  
## <a name="description"></a>Description  

 Geçici katılımcı Işlemeye veya durdurmaya karar verdiğinde, ancak belirli bir süre içinde bir COMMIT veya Rollback isteğine yanıt vermediğini izlendi.  
  
## <a name="troubleshooting"></a>Sorun giderme  

 Tüm geçici katılımcıların verilen süre içinde yanıt verebilmesini sağlayın. Varsayılan zaman aralığı 180 saniyedir.  Bu yeterli değilse, `VolatileOutcomeDelay` ws-at zamanlayıcı ilkesini artırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzleme](index.md)
- [Uygulamanızda Sorun Giderme için İzleme Kullanma](using-tracing-to-troubleshoot-your-application.md)
- [Yönetim ve tanılama](../index.md)
