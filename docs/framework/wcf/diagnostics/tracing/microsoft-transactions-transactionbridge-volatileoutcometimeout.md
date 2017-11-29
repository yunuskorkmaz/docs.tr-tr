---
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1992a209bb58c0a0d6f181eb2f1ec546d50372ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a>Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
WS-AT protokolü hizmetini geçici katılımcı sonucu iletisine yanıt beklerken zaman aşımına uğradı. Katılımcı döndürürse, işlem sonucu şüpheli olabilir.  
  
## <a name="description"></a>Açıklama  
 İzlenen Volatile katılımcı tamamlama veya iptal etmeye karar ancak belirli bir süre içinde bir yürütme veya geri alma isteğine yanıt vermedi.  
  
## <a name="troubleshooting"></a>Sorun giderme  
 Tüm Volatile katılımcılar verilen sürede yanıt verebilmesini olduğundan emin olun. Varsayılan süre 180 saniyedir.  Bu yetersiz ise artırmak `VolatileOutcomeDelay` WS-AT için Zamanlayıcı ilkesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Uygulamanızda sorun giderme için izlemeyi kullanma](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Yönetim ve tanılama](../../../../../docs/framework/wcf/diagnostics/index.md)
