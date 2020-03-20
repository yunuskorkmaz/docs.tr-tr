---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: e80fecf508158dcb53f08b75c8f9486c13e403a4
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674794"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a>System.ServiceModel.Channels.MsmqMessageDropped
MSMQ iletiyi bıraktı.  
  
## <a name="description"></a>Açıklama  
 İzleme, bir MSMQ iletisinin bırakıldığını gösterir. MsMQ iletileri, Windows Communication Foundation (WCF) (NetMsmqBinding veya MsmqIntegrationBinding ile birlikte kullanılır) bunları işleyemediğinde bırakılabilir. Bu tür iletilere zehirli iletiler denir.  
  
 NetMsmqBinding veya `ReceiveErrorHandling` MsmqIntegrationBinding üzerindeki özellik ayarlandığında bir zehir `Drop`iletisi bırakılır. Bırakılan ileti kuyruktan kaldırılır ve artık kurtarılamaz.  
  
 İletilerin ne zaman zehirhaline geldiği ve hizmetinizi uygun şekilde işlemek üzere nasıl yapılandırılacağı hakkında daha fazla bilgi için [Poison-Message Handling](../../feature-details/poison-message-handling.md)'e bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Uygulamanızda Sorun Giderme için İzleme Kullanma](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Yönetim ve Tanılama](../../../../../docs/framework/wcf/diagnostics/index.md)
- [Zehir-Mesaj Taşıma](../../feature-details/poison-message-handling.md)
