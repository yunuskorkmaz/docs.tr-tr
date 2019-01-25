---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: 3b51a100677221866186b2e24f34396c012d11c1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603137"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a>Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
WS-AT protokolü hizmetini hazırlama için yanıt vermedi dayanıklı bir katılımcı yeniden yürütme iletisi aldı. Sonuç olarak, işlem iptal edildi.  
  
## <a name="description"></a>Açıklama  
 Dayanıklı bir katılımcı hala hazırlama sırasında yeniden yürütme iletisi aldıysanız izlenen. Bu durum için geçersiz bir ileti budur ve işlem iptal edecek.  
  
## <a name="troubleshooting"></a>Sorun giderme  
 Bu hatanın hareketin sonucu emin değilseniz ancak (alt TransactionManagers dahil) dayanıklı bir katılımcı hata durumundan kurtuldu indiate olabilir ve durumunu istek.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Uygulamanızda Sorun Giderme için İzleme Kullanma](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Yönetim ve Tanılama](../../../../../docs/framework/wcf/diagnostics/index.md)
