---
title: Güvenlik Doğrulama ve Kimlik Doğrulama Hataları
ms.date: 03/30/2017
ms.assetid: 0d4e3666-dfc6-421c-baf8-9479c22f7050
ms.openlocfilehash: 32a7d41f93dd99f1950a073e1cac1b62177ff6c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916051"
---
# <a name="security-validation-and-authentication-failures"></a>Güvenlik Doğrulama ve Kimlik Doğrulama Hataları
Sayaç adı: Güvenlik Doğrulama ve Kimlik Doğrulama Hataları  
  
## <a name="description"></a>Açıklama  
 Her bir ileti "Güvenlik çağrıları yetkilendirilmedi" sayacı tarafından kapsanmayan bir güvenlik sorunu nedeniyle reddedilmesi Bu sayaç artırılır. Bu tür sorunlar şunlardır:  
  
- İstemci belirteci iletiden okunamıyor.  
  
- İstemci belirteci (örneğin, hatalı parola) kimlik doğrulaması başarısız oldu.  
  
- İmza doğrulaması başarısız oldu (örneğin, iletiyi oynanmadığını).  
  
- İleti yeniden yürütme bir saldırı sırasında gerçekleşebilir bir önceki bir yineleniyor.  
  
- Bir şifre çözme hatası oluştu.  
  
- Gereken bazı öğeleri (örneğin, eksik bir zaman damgası veya şifrelenmiş veriler engelle) gelen iletiyi yok.  
  
- TLSNEGO/SPNEGO anlaşması sırasında hatalar oluştu.
