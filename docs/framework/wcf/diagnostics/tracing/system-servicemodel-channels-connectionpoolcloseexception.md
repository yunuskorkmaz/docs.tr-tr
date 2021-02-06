---
description: ': System. ServiceModel. Channels. ConnectionPoolCloseException hakkında daha fazla bilgi edinin'
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: a65739cc872f3cd175d76e9113380f9f4185d498
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99644638"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a>System.ServiceModel.Channels.ConnectionPoolCloseException

Bu bağlantı havuzundaki bağlantılar kapatılırken bir özel durum oluştu.  
  
## <a name="description"></a>Description  

 Bu hata düzeyi izleme, Windows Communication Foundation (WCF) bağlantı havuzu özelliği tarafından kullanılan bağlantı havuzlarını kapatırken bir hata oluştuğunu gösterir. Bunun olası bir nedeni, havuza alınmış bir bağlantının başarısız bir kapanışı veya CloseTimeout içindeki bir havuza alınmış bağlantı kümesidir. Bu özel durum oluştuğunda, bu havuzun içindeki kalan kapatılmamış bağlantılar iptal edilir; diğer havuzların içindeki kapatılmamış bağlantılar bırakıldı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzleme](index.md)
- [Uygulamanızda Sorun Giderme için İzleme Kullanma](using-tracing-to-troubleshoot-your-application.md)
- [Yönetim ve tanılama](../index.md)
