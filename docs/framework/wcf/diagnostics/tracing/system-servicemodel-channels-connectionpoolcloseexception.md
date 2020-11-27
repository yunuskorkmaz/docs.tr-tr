---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: d8edb8e916578247e62e3a3eb3b11b80f93416cd
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286961"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a>System.ServiceModel.Channels.ConnectionPoolCloseException

Bu bağlantı havuzundaki bağlantılar kapatılırken bir özel durum oluştu.  
  
## <a name="description"></a>Açıklama  

 Bu hata düzeyi izleme, Windows Communication Foundation (WCF) bağlantı havuzu özelliği tarafından kullanılan bağlantı havuzlarını kapatırken bir hata oluştuğunu gösterir. Bunun olası bir nedeni, havuza alınmış bir bağlantının başarısız bir kapanışı veya CloseTimeout içindeki bir havuza alınmış bağlantı kümesidir. Bu özel durum oluştuğunda, bu havuzun içindeki kalan kapatılmamış bağlantılar iptal edilir; diğer havuzların içindeki kapatılmamış bağlantılar bırakıldı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzleme](index.md)
- [Uygulamanızda Sorun Giderme için İzleme Kullanma](using-tracing-to-troubleshoot-your-application.md)
- [Yönetim ve tanılama](../index.md)
