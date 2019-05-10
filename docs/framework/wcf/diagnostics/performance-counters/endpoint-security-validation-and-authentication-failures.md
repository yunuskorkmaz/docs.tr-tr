---
title: 'Uç noktası: Güvenlik Doğrulama ve Kimlik Doğrulama Hataları'
ms.date: 03/30/2017
ms.assetid: 5bad60aa-6084-4c7b-aefd-9b581f04382e
ms.openlocfilehash: 9e0192ea600bb52abd555f2f83cfe8e96d3fe203
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619336"
---
# <a name="endpoint-security-validation-and-authentication-failures"></a>Uç noktası: Güvenlik Doğrulama ve Kimlik Doğrulama Hataları
Sayaç adı: Güvenlik Doğrulama ve Kimlik Doğrulama Hataları  
  
## <a name="description"></a>Açıklama  
 Her bir ileti "Güvenlik çağrıları yetkilendirilmedi" sayacı tarafından kapsanmayan bir güvenlik sorunu nedeniyle reddedilmesi Bu sayaç artırılır. Bu tür sorunlar şunlardır:  
  
- İstemci belirteci iletiden okunamıyor.  
  
- İstemci belirteci (hatalı parola) kimlik doğrulaması başarısız oldu.  
  
- İmza doğrulaması başarısız oldu. (ileti oynanmış).  
  
- İleti yeniden yürütme bir saldırı sırasında gerçekleşebilir bir önceki bir yineleniyor.  
  
- Bir şifre çözme hatası oluştu.  
  
- İleti (zaman damgası veya şifrelenmiş veri bloğu eksik) bazı gerekli öğeleri eksik.  
  
- TLSNEGO/SPNEGO anlaşması sırasında hatalar oluştu.
