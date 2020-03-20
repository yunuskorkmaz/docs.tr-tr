---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: f89dd1373d67714046f8cb958582c3a5dea04456
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674786"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a>System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
İletiyi taşıyamaz veya silemez.  
  
## <a name="description"></a>Açıklama  
 İzleme, bir MSMQ iletisini taşımaya, silmeye veya reddetmeye çalışırken bir hata oluştuğunu gösterir.  
  
 MSMQ iletileri Windows Communication Foundation (WCF) tarafından kullanılır (NetMsmqBinding veya MsmqIntegrationBinding ile birlikte kullanıldığında). Bu izleme, NetMsmqBinding `ReceiveErrorHandling` veya MsmqIntegrationBinding üzerinde özelliğin seçilen değeri ile ilgilidir.  
  
 Bu izleme, genel bir sistem hatasının göstergesi değildir. Ancak, seçilen zehirli ileti nin bir ileti için başarısız olduğunu gösterir. İletilerin ne zaman zehirhaline geldiği ve hizmetinizi uygun şekilde işlemek üzere nasıl yapılandırılacağı hakkında daha fazla bilgi için [Poison-Message Handling](../../feature-details/poison-message-handling.md)'e bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Uygulamanızda Sorun Giderme için İzleme Kullanma](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Yönetim ve Tanılama](../../../../../docs/framework/wcf/diagnostics/index.md)
