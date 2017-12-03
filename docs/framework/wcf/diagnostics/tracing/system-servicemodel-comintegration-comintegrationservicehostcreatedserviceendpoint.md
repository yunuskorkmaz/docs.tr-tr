---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 474895e7fbcf1b9ed7ad7da6d28313ae4894f720
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a>System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
Taşıyamaz veya ileti silemezsiniz.  
  
## <a name="description"></a>Açıklama  
 İzleme, bir hata taşımak, silmek veya bir MSMQ iletisi reddetme çalışılırken zaman oluştuğunu gösterir.  
  
 MSMQ iletileri tarafından işe [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (NetMsmqBinding veya MsmqIntegrationBinding ile kullanıldığında). Bu izleme için seçilen değeri ilgili `ReceiveErrorHandling` NetMsmqBinding ya da MsmqIntegrationBinding özelliği.  
  
 Bu izleme genel bir sistem hatası göstergesi değil. Ancak, seçilen bir ileti başarısız oldu ileti değerlendirme zehirli gösterir. Bkz: [Poison ileti işleme](http://go.microsoft.com/fwlink/?LinkID=99546) iletileri ne zaman zararlı hale gelir ve uygun şekilde işlemek üzere, hizmetinin nasıl yapılandırılacağı hakkında daha fazla ayrıntı için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Uygulamanızda sorun giderme için izlemeyi kullanma](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Yönetim ve tanılama](../../../../../docs/framework/wcf/diagnostics/index.md)
