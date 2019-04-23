---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: 3dd28276cd3a39497c0387f5b9d0adec23d07c37
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182201"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a>System.ServiceModel.Channels.ConnectionPoolCloseException
Bu bağlantı havuzundaki bağlantı kapatılırken bir özel durum oluştu.  
  
## <a name="description"></a>Açıklama  
 Bu hata düzeyi izleme özelliğini Windows Communication Foundation (WCF) ait bağlantı tarafından kullanılan bağlantı havuzları kapatılırken bir hata oluştu gösterir. Bunun olası bir nedeni, havuza alınmış bir bağlantının başarısız bir kapanış veya havuza alınmış bağlantıları CloseTimeout içinde bir dizi ' dir. Bu özel durum oluştuğunda, bu havuz içindeki kalan tüm kapatılmamış bağlantıları iptal edilir; içindeki diğer havuzlara kapatılmamış bağlantılar yayını bırakıldı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Uygulamanızda Sorun Giderme için İzleme Kullanma](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Yönetim ve Tanılama](../../../../../docs/framework/wcf/diagnostics/index.md)
