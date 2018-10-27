---
title: 'Hizmet: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hataları'
ms.date: 03/30/2017
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
ms.openlocfilehash: ba8da3ae6be6bd089690359f19e153da1e0b54fc
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50039997"
---
# <a name="service-security-validation-and-authentication-failures"></a>Hizmet: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hataları
Sayaç adı: güvenlik doğrulaması ve kimlik doğrulaması hataları  
  
## <a name="description"></a>Açıklama  
 Her bir ileti "Güvenlik çağrıları yetkilendirilmedi" sayacı tarafından kapsanmayan bir güvenlik sorunu nedeniyle reddedilmesi Bu sayaç artırılır. Bu tür sorunlar şunlardır:  
  
-   İstemci belirteci iletiden okunamıyor.  
  
-   İstemci belirteci (örneğin, hatalı parola) kimlik doğrulaması başarısız oldu.  
  
-   İmza doğrulaması başarısız oldu (örneğin, iletiyi oynanmadığını).  
  
-   İleti yeniden yürütme bir saldırı sırasında gerçekleşebilir bir önceki bir yineleniyor.  
  
-   Bir şifre çözme hatası oluştu.  
  
-   Gereken bazı öğeleri (örneğin, eksik bir zaman damgası veya şifrelenmiş veriler engelleme) gelen iletiyi yok.  
  
-   TLSNEGO/SPNEGO anlaşması sırasında hatalar oluştu.
