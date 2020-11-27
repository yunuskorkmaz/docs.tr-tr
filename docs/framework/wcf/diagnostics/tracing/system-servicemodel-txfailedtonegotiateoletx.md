---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.date: 03/30/2017
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
ms.openlocfilehash: 7b468a57409e9a473a5bbf8e3324435e65e8c60b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96295320"
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
