---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: aeeba38eaf674453f4c87cf62f5088c55b5fde2d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96290822"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a>System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed

İleti taşınamıyor ya da silinemiyor.  
  
## <a name="description"></a>Açıklama  

 İzleme, bir MSMQ iletisini taşımaya, silmeye veya reddetmeye çalışırken bir hata oluştuğunu gösterir.  
  
 MSMQ iletileri Windows Communication Foundation (WCF) tarafından (NetMsmqBinding veya MsmqIntegrationBinding ile kullanıldığında) tarafından kullanılır. Bu izleme, `ReceiveErrorHandling` NetMsmqBinding veya MsmqIntegrationBinding üzerinde özelliğin seçili değeri ile ilgilidir.  
  
 Bu izleme, bir genel sistem hatasının göstergesidir. Ancak, seçilen zarar iletisi değerlendirmesi bir ileti için başarısız olduğunu gösterir. İletiler ne zaman zarar haline geldiği ve hizmetinizi uygun şekilde işleyecek şekilde yapılandırma hakkında daha fazla bilgi için bkz. [Poison-Message Handling](../../feature-details/poison-message-handling.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzleme](index.md)
- [Uygulamanızda Sorun Giderme için İzleme Kullanma](using-tracing-to-troubleshoot-your-application.md)
- [Yönetim ve tanılama](../index.md)
