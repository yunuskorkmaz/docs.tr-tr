---
title: Microsoft.Transactions.TransactionBridge.CommitMessageRetry
ms.date: 03/30/2017
ms.assetid: 4abe01f0-6398-4fba-b2f3-c054b7f7e971
ms.openlocfilehash: 28b83b293570adf3b1cfdc15c77afd0f0cf768eb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96259031"
---
# <a name="microsofttransactionstransactionbridgecommitmessageretry"></a>Microsoft.Transactions.TransactionBridge.CommitMessageRetry

Bir tamamlama iletisi yeniden denemesi, yanıt vermeyen bir katılımcıya gönderildi.  
  
## <a name="description"></a>Açıklama  

 Yerel Işlem yöneticisinin belirli bir süre içinde yanıt almadığı için bir Işleme iletisini bir alt katılımcıya yeniden göndermesi gerekiyorsa izleniyor.  
  
## <a name="troubleshooting"></a>Sorun giderme  

 Yanıtın zamanında teslim edilmesini önleyen olası ağ veya ürün sorunlarını araştırın.  Bu mesajların birçoğu görülemiyorsa, altyapı sorunları veya anormal bir şekilde uzun yanıt süreleri belirtebilir. Her iki sorun da sistem içindeki işlemlerin verimini büyük ölçüde azaltır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzleme](index.md)
- [Uygulamanızda Sorun Giderme için İzleme Kullanma](using-tracing-to-troubleshoot-your-application.md)
- [Yönetim ve tanılama](../index.md)
