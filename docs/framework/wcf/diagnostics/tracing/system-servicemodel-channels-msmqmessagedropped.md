---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1d4b819b47d682a81bdcc031cc6b09604b072be7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a>System.ServiceModel.Channels.MsmqMessageDropped
MSMQ İleti bırakıldı.  
  
## <a name="description"></a>Açıklama  
 İzleme, bir MSMQ İleti bırakıldı gösterir. MSMQ iletileri bırakılan ne zaman [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (NetMsmqBinding ya da MsmqIntegrationBinding ile kullanılır) bunları işleyemiyor. Bu türden iletilere zarar iletileri adlandırılır.  
  
 Zararlı bir ileti olduğunda bırakılan `ReceiveErrorHandling` NetMsmqBinding ya da MsmqIntegrationBinding özelliği ayarlanmış `Drop`. Bırakılan ileti kuyruktan kaldırılır ve artık kurtarılabilir.  
  
 Bkz: [Poison ileti işleme](http://go.microsoft.com/fwlink/?LinkID=99546) iletileri ne zaman zararlı hale gelir ve uygun şekilde işlemek üzere, hizmetinin nasıl yapılandırılacağı hakkında daha fazla ayrıntı için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Uygulamanızda sorun giderme için izlemeyi kullanma](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Yönetim ve tanılama](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [Poison ileti işleme](http://go.microsoft.com/fwlink/?LinkID=99546)
