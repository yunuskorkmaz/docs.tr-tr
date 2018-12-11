---
title: 'Hizmet: Güvenlik Doğrulama ve Kimlik Doğrulama Hataları'
ms.date: 03/30/2017
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
ms.openlocfilehash: ba8da3ae6be6bd089690359f19e153da1e0b54fc
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53150907"
---
# <a name="service-security-validation-and-authentication-failures"></a>Hizmet: Güvenlik Doğrulama ve Kimlik Doğrulama Hataları
Sayaç adı: Güvenlik Doğrulama ve Kimlik Doğrulama Hataları  
  
## <a name="description"></a>Açıklama  
 Her bir ileti "Güvenlik çağrıları yetkilendirilmedi" sayacı tarafından kapsanmayan bir güvenlik sorunu nedeniyle reddedilmesi Bu sayaç artırılır. Bu tür sorunlar şunlardır:  
  
-   İstemci belirteci iletiden okunamıyor.  
  
-   İstemci belirteci (örneğin, hatalı parola) kimlik doğrulaması başarısız oldu.  
  
-   İmza doğrulaması başarısız oldu (örneğin, iletiyi oynanmadığını).  
  
-   İleti yeniden yürütme bir saldırı sırasında gerçekleşebilir bir önceki bir yineleniyor.  
  
-   Bir şifre çözme hatası oluştu.  
  
-   Gereken bazı öğeleri (örneğin, eksik bir zaman damgası veya şifrelenmiş veriler engelleme) gelen iletiyi yok.  
  
-   TLSNEGO/SPNEGO anlaşması sırasında hatalar oluştu.
