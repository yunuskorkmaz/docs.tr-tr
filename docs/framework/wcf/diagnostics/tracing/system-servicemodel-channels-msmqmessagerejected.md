---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3194409ef6daf417d3643eed20afa18944e29ad3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a>System.ServiceModel.Channels.MsmqMessageRejected
MSMQ İleti reddedildi.  
  
## <a name="description"></a>Açıklama  
 Bu izleme, bir MSMQ İleti reddedildi gösterir.  
  
 MSMQ iletileri olabilir ne zaman reddedilen [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (NetMsmqBinding ya da MsmqIntegrationBinding ile kullanılır) bunları işleyemiyor. Bu türden iletilere zarar iletileri adlandırılır. Zararlı bir ileti reddedildi zaman `ReceiveErrorHandling` NetMsmqBinding ya da MsmqIntegrationBinding özelliği ayarlanmış `Reject`. Reddedilen ileti geri gönderen için teslim [sahipsiz sırayı](http://go.microsoft.com/fwlink/?LinkID=99544).  
  
 Bkz: [Poison ileti işleme](http://go.microsoft.com/fwlink/?LinkID=99546) iletileri ne zaman zararlı hale gelir ve uygun şekilde işlemek üzere, hizmetinin nasıl yapılandırılacağı hakkında daha fazla ayrıntı için.  
  
 Bkz: [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548) MSMQ reddedilen ileti anlamı hakkında daha fazla bilgi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Uygulamanızda sorun giderme için izlemeyi kullanma](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Yönetim ve tanılama](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [Poison ileti işleme](http://go.microsoft.com/fwlink/?LinkID=99546)  
 [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548)
