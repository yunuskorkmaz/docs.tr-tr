---
description: 'Daha fazla bilgi edinin: uç nokta: güvenlik doğrulama ve kimlik doğrulama sorunları'
title: 'Uç Noktası: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hataları'
ms.date: 03/30/2017
ms.assetid: 5bad60aa-6084-4c7b-aefd-9b581f04382e
ms.openlocfilehash: 9131eebcf85032c591ebf7f65e2b0e5f67ec60df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99655430"
---
# <a name="endpoint-security-validation-and-authentication-failures"></a>Uç Noktası: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hataları

Sayaç adı: güvenlik doğrulama ve kimlik doğrulama sorunları  
  
## <a name="description"></a>Description  

 Bu sayaç, "güvenlik çağrıları yetkilendirilmemiş" sayacı kapsamında olmayan bir güvenlik sorunu nedeniyle her ileti reddedildiğinde artırılır. Bu tür sorunlar şunlardır:  
  
- İstemci belirteci iletiden okunamıyor.  
  
- İstemci belirteci kimlik doğrulaması başarısız oldu (hatalı parola).  
  
- İmza doğrulama başarısız oldu (ileti değiştirilmiş).  
  
- İleti, bir yeniden yürütme saldırısında meydana gelebilen bir öncekinden yineleniyor.  
  
- Şifre çözme hatası oluştu.  
  
- İletide bazı gerekli öğeler (eksik zaman damgası veya şifrelenmiş veri bloğu) eksik.  
  
- TLSNEGO/SPNEGO Handshake sırasında hatalar oluştu.
