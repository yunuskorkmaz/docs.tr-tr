---
title: 'Uç Noktası: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hataları'
ms.date: 03/30/2017
ms.assetid: 5bad60aa-6084-4c7b-aefd-9b581f04382e
author: BrucePerlerMS
ms.openlocfilehash: f7cd2268eefa0176ab71a3d5d3bc82c178664742
ms.sourcegitcommit: daa8788af67ac2d1cecd24f9f3409babb2f978c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47862808"
---
# <a name="endpoint-security-validation-and-authentication-failures"></a>Uç Noktası: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hataları
Sayaç adı: güvenlik doğrulaması ve kimlik doğrulaması hataları  
  
## <a name="description"></a>Açıklama  
 Her bir ileti "Güvenlik çağrıları yetkilendirilmedi" sayacı tarafından kapsanmayan bir güvenlik sorunu nedeniyle reddedilmesi Bu sayaç artırılır. Bu tür sorunlar şunlardır:  
  
-   İstemci belirteci iletiden okunamıyor.  
  
-   İstemci belirteci (hatalı parola) kimlik doğrulaması başarısız oldu.  
  
-   İmza doğrulaması başarısız oldu. (ileti oynanmış).  
  
-   İleti yeniden yürütme bir saldırı sırasında gerçekleşebilir bir önceki bir yineleniyor.  
  
-   Bir şifre çözme hatası oluştu.  
  
-   İleti (zaman damgası veya şifrelenmiş veri bloğu eksik) bazı gerekli öğeleri eksik.  
  
-   TLSNEGO/SPNEGO anlaşması sırasında hatalar oluştu.
