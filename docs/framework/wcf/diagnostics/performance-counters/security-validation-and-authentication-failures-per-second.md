---
title: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hatası/Saniye
ms.date: 03/30/2017
ms.assetid: 266c3bd3-2ffc-4471-94b7-3675443be1ac
ms.openlocfilehash: c64c121550043127db674fac6287a870449d789d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253134"
---
# <a name="security-validation-and-authentication-failures-per-second"></a>Güvenlik Doğrulaması ve Kimlik Doğrulaması Hatası/Saniye

Sayaç adı: saniye başına güvenlik doğrulaması ve kimlik doğrulama başarısızlığı.  
  
## <a name="description"></a>Açıklama  

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
