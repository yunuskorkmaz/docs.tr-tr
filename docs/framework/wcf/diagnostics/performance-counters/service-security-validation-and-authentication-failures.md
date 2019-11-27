---
title: 'Hizmet: Güvenlik Doğrulama ve Kimlik Doğrulama Hataları'
ms.date: 03/30/2017
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
ms.openlocfilehash: 399249926bcb1383fd33f60510c2c212c6f4261c
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204574"
---
# <a name="service-security-validation-and-authentication-failures"></a>Hizmet: Güvenlik Doğrulama ve Kimlik Doğrulama Hataları
Sayaç adı: güvenlik doğrulama ve kimlik doğrulama sorunları  
  
## <a name="description"></a>Açıklama  
 Bu sayaç, "güvenlik çağrıları yetkilendirilmemiş" sayacı kapsamında olmayan bir güvenlik sorunu nedeniyle her ileti reddedildiğinde artırılır. Bu tür sorunlar şunlardır:  
  
- İstemci belirteci iletiden okunamıyor.  
  
- İstemci belirteci kimlik doğrulaması başarısız oldu (örneğin, hatalı parola).  
  
- İmza doğrulama başarısız oldu (örneğin, ileti değiştirilmiş).  
  
- İleti, bir yeniden yürütme saldırısında meydana gelebilen bir öncekinden yineleniyor.  
  
- Şifre çözme hatası oluştu.  
  
- İletide bazı gerekli öğeler (örneğin, eksik zaman damgası veya şifrelenmiş veri bloğu) eksik.  
  
- TLSNEGO/SPNEGO Handshake sırasında hatalar oluştu.
