---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: 0a28eec659b48d5add4c53bc8c16972892e65099
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487912"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a>System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
Taşıyamaz veya ileti silemezsiniz.  
  
## <a name="description"></a>Açıklama  
 İzleme, bir hata taşımak, silmek veya bir MSMQ iletisi reddetme çalışılırken zaman oluştuğunu gösterir.  
  
 MSMQ iletileri tarafından Windows Communication Foundation ((NetMsmqBinding veya MsmqIntegrationBinding ile kullanıldığında) WCF) görevli olduğu. Bu izleme için seçilen değeri ilgili `ReceiveErrorHandling` NetMsmqBinding ya da MsmqIntegrationBinding özelliği.  
  
 Bu izleme genel bir sistem hatası göstergesi değil. Ancak, seçilen bir ileti başarısız oldu ileti değerlendirme zehirli gösterir. Bkz: [Poison ileti işleme](http://go.microsoft.com/fwlink/?LinkID=99546) iletileri ne zaman zararlı hale gelir ve uygun şekilde işlemek üzere, hizmetinin nasıl yapılandırılacağı hakkında daha fazla ayrıntı için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Uygulamanızda Sorun Giderme için İzleme Kullanma](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Yönetim ve Tanılama](../../../../../docs/framework/wcf/diagnostics/index.md)
