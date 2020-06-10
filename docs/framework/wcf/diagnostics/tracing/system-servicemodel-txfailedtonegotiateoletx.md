---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.date: 03/30/2017
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
ms.openlocfilehash: 2c9ea77cdd76d4593c2ee5b09a4b917677b8925f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601419"
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a>System.ServiceModel.TxFailedToNegotiateOleTx
OleTransactions protokol anlaşması belirtilen düzenleme bağlamı için başarısız oldu.  
  
## <a name="description"></a>Açıklama  
 OleTx bilgilerine sahip bir gelen işlem eklenen OleTx bilgilerini kullanamadığı ve bunun yerine WS-AT kullanmaya geri dönecektir.  
  
## <a name="troubleshooting"></a>Sorun giderme  
 Makineler arasındaki MSDTC RPC iletişimi ile ilgili olası bir sorunu gösterir. Bu İzlemelerden birçoğu günlükte görünüyorsa, performansın çok fazla azalmasını sağlayabilir.  OleTx istenmiyorsa, `OleTxUpgradeEnabled` ws-at kayıt defteri yapılandırmasında 0 olarak ayarlayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzleme](index.md)
- [Uygulamanızda Sorun Giderme için İzleme Kullanma](using-tracing-to-troubleshoot-your-application.md)
- [Yönetim ve tanılama](../index.md)
