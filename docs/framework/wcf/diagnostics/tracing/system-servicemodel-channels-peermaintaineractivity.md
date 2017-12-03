---
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 71bcb16b89934f7f04cfd7d2f3c4b0ef3009dd78
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a>System.ServiceModel.Channels.PeerMaintainerActivity
PeerMaintainer Modülü (izleme ileti gövdesi içinde ayrıntıları) belirli bir işlemi gerçekleştiriyor.  
  
## <a name="description"></a>Açıklama  
 Bu izleme, çeşitli PeerMaintainer işlemleri sırasında oluşur.  
  
 PeerMaintainer PeerNode iç bir bileşenidir. Dakikada ya da aldığınız her 32 iletileri LinkUtility iletisi Komşuları istatistiklerle birlikte kaç iletileri hakkında değiştirilir ve yararlı (olmayan-untampered yinelemeleri) kaç gönderir. Bu, belirli komşu 's bağlantı yardımcı programı belirlenmesine yardımcı olur. Yaklaşık her beş dakikada Bakımcı komşu bağlantıları durumunu denetler. Komşu bağlantıları sayısı ideal miktarını aşarsa Bakımcı az yararlı bağlantıları ayıklar. Yeterli bağlantıları değilse Bakımcı yeni bağlantıları edinir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Uygulamanızda sorun giderme için izlemeyi kullanma](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Yönetim ve tanılama](../../../../../docs/framework/wcf/diagnostics/index.md)
