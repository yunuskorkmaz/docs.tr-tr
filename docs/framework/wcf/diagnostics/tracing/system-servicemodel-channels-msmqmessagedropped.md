---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: ad05a2b8552cc09d45e950e2c3336d86be918963
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33479137"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a>System.ServiceModel.Channels.MsmqMessageDropped
MSMQ İleti bırakıldı.  
  
## <a name="description"></a>Açıklama  
 İzleme, bir MSMQ İleti bırakıldı gösterir. Windows Communication Foundation (WCF) (NetMsmqBinding ya da MsmqIntegrationBinding ile kullanılır) işlemek başlatılamadığında MSMQ iletileri bırakılabilir. Bu türden iletilere zarar iletileri adlandırılır.  
  
 Zararlı bir ileti olduğunda bırakılan `ReceiveErrorHandling` NetMsmqBinding ya da MsmqIntegrationBinding özelliği ayarlanmış `Drop`. Bırakılan ileti kuyruktan kaldırılır ve artık kurtarılabilir.  
  
 Bkz: [Poison ileti işleme](http://go.microsoft.com/fwlink/?LinkID=99546) iletileri ne zaman zararlı hale gelir ve uygun şekilde işlemek üzere, hizmetinin nasıl yapılandırılacağı hakkında daha fazla ayrıntı için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Uygulamanızda Sorun Giderme için İzleme Kullanma](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Yönetim ve Tanılama](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [Poison ileti işleme](http://go.microsoft.com/fwlink/?LinkID=99546)
