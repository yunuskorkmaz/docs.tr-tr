---
title: Microsoft.Transactions.TransactionBridge.CommitMessageRetry
ms.date: 03/30/2017
ms.assetid: 4abe01f0-6398-4fba-b2f3-c054b7f7e971
ms.openlocfilehash: d939d525fd1c7e8f41cccbc3ca7af9726f22bdfc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54571437"
---
# <a name="microsofttransactionstransactionbridgecommitmessageretry"></a>Microsoft.Transactions.TransactionBridge.CommitMessageRetry
Bir işleme iletisi yeniden deneme yanıt vermeyen bir katılımcı gönderildi.  
  
## <a name="description"></a>Açıklama  
 Yerel hareket yöneticisi belirli bir süre içinde bir yanıt almadığı için bir işleme iletisi bağımlı Katılımcısı yeniden göndermeniz gerekirse izlenen.  
  
## <a name="troubleshooting"></a>Sorun giderme  
 Olası ağ veya tarihte teslim edilen gelen yanıt engelleyen ürün sorunları araştırın.  Bu iletiler birçoğu görülürse, altyapı sorunları veya aşırı uzun yanıt süreleri belirtebilirsiniz. Her iki sorun sistemi içinde işlemlerinin aktarım hızını ciddi ölçüde düşürüyor.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Uygulamanızda Sorun Giderme için İzleme Kullanma](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Yönetim ve Tanılama](../../../../../docs/framework/wcf/diagnostics/index.md)
