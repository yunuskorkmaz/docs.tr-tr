---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6c0e688e1f24171494b4adaae964ac1fc2be2309
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a>System.ServiceModel.TxFailedToNegotiateOleTx
OleTransactions Protokolü anlaşması için belirtilen koordinasyon bağlamı tamamlayamadı.  
  
## <a name="description"></a>Açıklama  
 Gelen bir işlem OleTx bilgilerle eklenen OleTx bilgiler kullanamadı ve sonbaharda WS-AT kullanmaya geri izlenen.  
  
## <a name="troubleshooting"></a>Sorun giderme  
 MSDTC RPC iletişimi makineler arasındaki olası bir sorun olduğunu gösterir. Bu izlemeler çoğunu günlüğünde görünür, performans kazanmadan ciddi bir düşüş ortaya çıkabilir.  OleTx değil istenirse, ayarlamak `OleTxUpgradeEnabled` 0 WS-AT kayıt defteri yapılandırma.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Uygulamanızda sorun giderme için izlemeyi kullanma](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Yönetim ve tanılama](../../../../../docs/framework/wcf/diagnostics/index.md)
