---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0ea98388efe14ac0d18a94ec056a441096a4d7c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a>System.ServiceModel.Channels.ConnectionPoolCloseException
Bu bağlantı havuzundaki bağlantılar kapatılırken bir özel durum oluştu.  
  
## <a name="description"></a>Açıklama  
 Bu hata düzeyi izleme tarafından kullanılan bağlantı havuzu kapatılırken bir hata oluştu gösterir [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]kullanıcının bağlantı havuzu özelliği. Havuza alınmış bağlantısının başarısız bir kapatma veya havuza alınan bağlantıları CloseTimeout içinde kümesi bu olası nedenlerden biri. Bu durum, aynı havuz içindeki kalan tüm kapatılmamış bağlantıları iptal edilir; diğer havuzlardaki kapatılmamış bağlantıları terk.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Uygulamanızda sorun giderme için izlemeyi kullanma](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Yönetim ve tanılama](../../../../../docs/framework/wcf/diagnostics/index.md)
