---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: 0a312d192546655dc327667c00f4f2bbc0c15fdb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602056"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a>System.ServiceModel.Channels.ConnectionPoolCloseException
Bu bağlantı havuzundaki bağlantılar kapatılırken bir özel durum oluştu.  
  
## <a name="description"></a>Açıklama  
 Bu hata düzeyi izleme, Windows Communication Foundation (WCF) bağlantı havuzu özelliği tarafından kullanılan bağlantı havuzlarını kapatırken bir hata oluştuğunu gösterir. Bunun olası bir nedeni, havuza alınmış bir bağlantının başarısız bir kapanışı veya CloseTimeout içindeki bir havuza alınmış bağlantı kümesidir. Bu özel durum oluştuğunda, bu havuzun içindeki kalan kapatılmamış bağlantılar iptal edilir; diğer havuzların içindeki kapatılmamış bağlantılar bırakıldı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzleme](index.md)
- [Uygulamanızda Sorun Giderme için İzleme Kullanma](using-tracing-to-troubleshoot-your-application.md)
- [Yönetim ve tanılama](../index.md)
