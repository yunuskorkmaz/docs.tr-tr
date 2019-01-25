---
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.date: 03/30/2017
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
ms.openlocfilehash: 4c352ad4ac4ffee5d12c054590ef994bab0ba757
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642587"
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a>System.ServiceModel.Channels.PeerMaintainerActivity
PeerMaintainer modülü, belirli bir işlemi (ayrıntıları izleme iletisi gövdesi içinde yer alan) gerçekleştiriyor.  
  
## <a name="description"></a>Açıklama  
 Bu izleme, çeşitli PeerMaintainer işlemleri sırasında gerçekleşir.  
  
 PeerMaintainer PeerNode iç bir bileşenidir. Dakika başı veya alınan her 32 ileti LinkUtility iletisi Komşuları istatistiklerle kaç mesajları hakkında ve ne kadar yararlı (olmayan-untampered yinelemeleri) gönderir. Bu, belirli bir komşunun bağlantısı yardımcı programı belirlenmesine yardımcı olur. Yaklaşık beş dakikada, Bakımcı komşu bağlantı durumunu denetler. Komşu bağlantı sayısını ideal miktarı aşarsa, Bakımcı az yararlı bağlantıları ayıklar. Yeterli bağlantı yoksa, yeni bağlantılar Bakımcı devralır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Uygulamanızda Sorun Giderme için İzleme Kullanma](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Yönetim ve Tanılama](../../../../../docs/framework/wcf/diagnostics/index.md)
