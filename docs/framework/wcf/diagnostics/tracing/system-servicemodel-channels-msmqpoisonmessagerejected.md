---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: 6b0e6e3ebcf5d414e9dbbcecd09ba2e8bb3ddd3a
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674810"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a>System.ServiceModel.Channels.MsmqPoisonMessageRejected
Zehirli ileti reddedildi.  
  
## <a name="description"></a>Açıklama  

 İz, zehirli bir iletiyle karşılaşıldığını ve daha sonra reddedildiğini gösterir. Bu, NetMsmqBinding veya MsmqIntegrationBinding'deki `ReceiveErrorHandling` özellik . `Reject` Reddedilen ileti gönderenin [Ölü Harf Kuyruğuna](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)geri teslim edilir.  
  
 İletilerin ne zaman zehirhaline geldiği ve hizmetinizi uygun şekilde işlemek üzere nasıl yapılandırılacağı hakkında daha fazla bilgi için [Poison-Message Handling](../../feature-details/poison-message-handling.md)'e bakın. Reddedilen iletinin MSMQ'da ne anlama geldiğini hakkında daha fazla bilgi [için](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))bkz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Uygulamanızda Sorun Giderme için İzleme Kullanma](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Yönetim ve Tanılama](../../../../../docs/framework/wcf/diagnostics/index.md)
- [Zehir-Mesaj Taşıma](../../feature-details/poison-message-handling.md)
- [MQMarkMessageReddedildi](https://docs.microsoft.com/previous-versions/windows/desktop/msmq/ms707071(v%3dvs.85))
