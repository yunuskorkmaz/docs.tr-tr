---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: ade49ceb86a401cd27a9381b1ea5d0c1ad624548
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623098"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a>System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
Taşınamıyor veya ileti Sil.  
  
## <a name="description"></a>Açıklama  
 İzleme taşımak, silmek veya bir MSMQ iletisinin reddetme çalışırken bir hata oluştuğunu gösterir.  
  
 MSMQ iletileri tarafından Windows Communication Foundation ((NetMsmqBinding veya MsmqIntegrationBinding ile kullanıldığında) WCF) çalışan. Bu izleme, seçili değerine ilgili `ReceiveErrorHandling` NetMsmqBinding veya MsmqIntegrationBinding özelliği.  
  
 Bu izleme genel bir sistem hatası göstergesi değil. Ancak, seçilen bir iletide başarısız oldu iletisi değerlendirme zehirli gösterir. Bkz: [Poison ileti işleme](https://go.microsoft.com/fwlink/?LinkID=99546) iletileri zehirli duruma ne zaman ve uygun şekilde işlemek için hizmetinizi yapılandırmak nasıl daha fazla ayrıntı için.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Uygulamanızda Sorun Giderme için İzleme Kullanma](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Yönetim ve Tanılama](../../../../../docs/framework/wcf/diagnostics/index.md)
