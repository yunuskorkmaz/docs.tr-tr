---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: 27402017e5e79194578719fd0c921dfc1e047b80
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43407923"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a>System.ServiceModel.Channels.MsmqPoisonMessageRejected
Zehirli ileti reddedildi.  
  
## <a name="description"></a>Açıklama  
 İzleme, zehirli ileti karşılaştı ve daha sonra reddedildiği olduğunu gösterir. Böyle durumlarda `ReceiveErrorHandling` özelliği NetMsmqBinding veya MsmqIntegrationBinding `Reject`. Reddedilen ileti geri gönderen için teslim [eski ileti sırası](https://go.microsoft.com/fwlink/?LinkId=99544).  
  
 Bkz: [Poison ileti işleme](https://go.microsoft.com/fwlink/?LinkId=99546) iletileri zehirli duruma ne zaman ve uygun şekilde işlemek için hizmetinizi yapılandırmak nasıl daha fazla ayrıntı için. Bkz: [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkId=99548) MSMQ reddedilen ileti ne anlama hakkında daha fazla bilgi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Uygulamanızda Sorun Giderme için İzleme Kullanma](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Yönetim ve Tanılama](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [Poison ileti işleme](https://go.microsoft.com/fwlink/?LinkId=99546)  
 [MQMarkMessageRejected](https://go.microsoft.com/fwlink/?LinkId=99548)
