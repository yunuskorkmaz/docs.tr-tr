---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.date: 03/30/2017
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
ms.openlocfilehash: 6aecc8f808d42c0096f6caef0574c72db6c53079
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528673"
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a>System.ServiceModel.TxFailedToNegotiateOleTx
Belirtilen düzenleme bağlamı OleTransactions Protokolü anlaşmasını tamamlayamadı.  
  
## <a name="description"></a>Açıklama  
 Gelen bir işlem OleTx bilgilerle eklenen OleTx bilgiler kullanamaz ve fall WS-AT bunun yerine geri izlenen.  
  
## <a name="troubleshooting"></a>Sorun giderme  
 MSDTC RPC iletişimi makineler arasındaki olası bir sorun olduğunu gösterir. Bu izlemeler birçoğu günlüğünde görünürse, güçlü bir performans düşüklüğü neden olabilir.  OleTx istenildiği gibi değilse, ayarlama `OleTxUpgradeEnabled` 0 WS-AT kayıt defteri yapılandırma.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Uygulamanızda Sorun Giderme için İzleme Kullanma](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Yönetim ve Tanılama](../../../../../docs/framework/wcf/diagnostics/index.md)
