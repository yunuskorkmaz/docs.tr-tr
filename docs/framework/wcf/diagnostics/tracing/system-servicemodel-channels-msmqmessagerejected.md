---
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: 2bd64263a2374c10a3514cbed75f9224542051dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33478952"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a>System.ServiceModel.Channels.MsmqMessageRejected
MSMQ İleti reddedildi.  
  
## <a name="description"></a>Açıklama  
 Bu izleme, bir MSMQ İleti reddedildi gösterir.  
  
 Windows Communication Foundation (WCF) (NetMsmqBinding ya da MsmqIntegrationBinding ile kullanılır) işlemek başlatılamadığında MSMQ iletileri reddedilebilir. Bu türden iletilere zarar iletileri adlandırılır. Zararlı bir ileti reddedildi zaman `ReceiveErrorHandling` NetMsmqBinding ya da MsmqIntegrationBinding özelliği ayarlanmış `Reject`. Reddedilen ileti geri gönderen için teslim [sahipsiz sırayı](http://go.microsoft.com/fwlink/?LinkID=99544).  
  
 Bkz: [Poison ileti işleme](http://go.microsoft.com/fwlink/?LinkID=99546) iletileri ne zaman zararlı hale gelir ve uygun şekilde işlemek üzere, hizmetinin nasıl yapılandırılacağı hakkında daha fazla ayrıntı için.  
  
 Bkz: [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548) MSMQ reddedilen ileti anlamı hakkında daha fazla bilgi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Uygulamanızda Sorun Giderme için İzleme Kullanma](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Yönetim ve Tanılama](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [Poison ileti işleme](http://go.microsoft.com/fwlink/?LinkID=99546)  
 [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkID=99548)
