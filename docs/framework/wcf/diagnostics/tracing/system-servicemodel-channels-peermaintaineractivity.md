---
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.date: 03/30/2017
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
ms.openlocfilehash: c1e82611bb776531ad3e3d60283d970602eb7f15
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293032"
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a>System.ServiceModel.Channels.PeerMaintainerActivity

Peerbakımcı modülü belirli bir işlemi gerçekleştiriyor (izleme iletisi gövdesinde bulunan Ayrıntılar).  
  
## <a name="description"></a>Açıklama  

 Bu izleme, çeşitli Peerbakımcı işlemleri sırasında oluşur.  
  
 Peerbakımcı, bir PeerNode iç bileşenidir. Her dakika veya alınan her 32 ileti, komşunlarına kaç tane ileti değiştirildiğini ve kaç tane yararlı olduğunu (yinelenmeyen, değiştirilmemiş) gösteren istatistiklerle bir LinkUtility iletisi gönderir. Bu, belirli bir komşunun bağlantı yardımcı programını belirlemesine yardımcı olur. Her beş dakikada bir, bakımcı, komşu bağlantıların sistem durumunu denetler. Komşu bağlantı sayısı ideal miktarı aşarsa, bakımcı en az faydalı bağlantıları ayıklar. Yeterli bağlantı yoksa, bakımcı yeni bağlantıları alır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzleme](index.md)
- [Uygulamanızda Sorun Giderme için İzleme Kullanma](using-tracing-to-troubleshoot-your-application.md)
- [Yönetim ve tanılama](../index.md)
