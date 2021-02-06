---
description: 'Şu konuda daha fazla bilgi edinin: uç nokta: güvenlik doğrulama ve saniyede kimlik doğrulama başarısızlığı'
title: 'Uç Noktası: Saniyede Güvenlik Doğrulama ve Kimlik Doğrulama Hatası'
ms.date: 03/30/2017
ms.assetid: 89a70b90-d7e4-4b03-9b84-4dc88ce3d605
ms.openlocfilehash: aa5ccc4049dc81a7c2d545cfc70e9078ac72d87a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99655441"
---
# <a name="endpoint-security-validation-and-authentication-failures-per-second"></a>Uç Noktası: Saniyede Güvenlik Doğrulama ve Kimlik Doğrulama Hatası

Sayaç adı: güvenlik doğrulaması ve saniye başına kimlik doğrulama başarısızlığı  
  
## <a name="description"></a>Description  

 Bu sayaç, "güvenlik çağrıları yetkilendirilmemiş" sayacı kapsamında olmayan bir güvenlik sorunu nedeniyle her ileti reddedildiğinde artırılır. Bu tür sorunlar şunlardır:  
  
- İstemci belirteci iletiden okunamıyor.  
  
- İstemci belirteci kimlik doğrulaması başarısız oldu (örneğin, hatalı parola).  
  
- İmza doğrulama başarısız oldu (örneğin, ileti değiştirilmiş).  
  
- İleti, bir yeniden yürütme saldırısında meydana gelebilen bir öncekinden yineleniyor.  
  
- Şifre çözme hatası oluştu.  
  
- İletide bazı gerekli öğeler (örneğin, eksik zaman damgası veya şifrelenmiş veri bloğu) eksik.  
  
- TLSNEGO/SPNEGO Handshake sırasında hatalar oluştu.  
  
 Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür:  
  
 (N1-N0)/((D1-D0)/F)
