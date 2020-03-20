---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: 8f783dcd4b966ed89c24d724918a3923c5a2d0b1
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674767"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a>System.ServiceModel.Channels.MsmqMessageRejected
MSMQ iletiyi reddetti.  
  
## <a name="description"></a>Açıklama  
 Bu izleme, bir MSMQ iletisi reddedildi gösterir.  
  
 MSMQ iletileri, Windows Communication Foundation (WCF) (NetMsmqBinding veya MsmqIntegrationBinding ile birlikte kullanılır) bunları işleyemediğinde reddedilebilir. Bu tür iletilere zehirli iletiler denir. NetMsmqBinding veya `ReceiveErrorHandling` MsmqIntegrationBinding'deki özellik `Reject`. Reddedilen ileti gönderenin [Ölü Harf Kuyruğuna](https://docs.microsoft.com/dotnet/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures)geri teslim edilir.  
  
 İletilerin ne zaman zehirhaline geldiği ve hizmetinizi uygun şekilde işlemek üzere nasıl yapılandırılacağı hakkında daha fazla bilgi için [Poison-Message Handling](../../feature-details/poison-message-handling.md)'e bakın.  
  
 Reddedilen iletinin MSMQ'da ne anlama geldiğini hakkında daha fazla bilgi [için](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))bkz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Uygulamanızda Sorun Giderme için İzleme Kullanma](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Yönetim ve Tanılama](../../../../../docs/framework/wcf/diagnostics/index.md)
- [Zehir-Mesaj Taşıma](../../feature-details/poison-message-handling.md)
- [MQMarkMessageReddedildi](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))
