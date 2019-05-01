---
title: 'Uç noktası: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hatası/Saniye'
ms.date: 03/30/2017
ms.assetid: 89a70b90-d7e4-4b03-9b84-4dc88ce3d605
ms.openlocfilehash: 43886f79585fb9a63eeb51360cc869365c100a1d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916545"
---
# <a name="endpoint-security-validation-and-authentication-failures-per-second"></a>Uç noktası: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hatası/Saniye
Sayaç adı: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hatası/Saniye  
  
## <a name="description"></a>Açıklama  
 Her bir ileti "Güvenlik çağrıları yetkilendirilmedi" sayacı tarafından kapsanmayan bir güvenlik sorunu nedeniyle reddedilmesi Bu sayaç artırılır. Bu tür sorunlar şunlardır:  
  
- İstemci belirteci iletiden okunamıyor.  
  
- İstemci belirteci (örneğin, hatalı parola) kimlik doğrulaması başarısız oldu.  
  
- İmza doğrulaması başarısız oldu (örneğin, iletiyi oynanmadığını).  
  
- İleti yeniden yürütme bir saldırı sırasında gerçekleşebilir bir önceki bir yineleniyor.  
  
- Bir şifre çözme hatası oluştu.  
  
- Gereken bazı öğeleri (örneğin, eksik bir zaman damgası veya şifrelenmiş veriler engelle) gelen iletiyi yok.  
  
- TLSNEGO/SPNEGO anlaşması sırasında hatalar oluştu.  
  
 Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır:  
  
 (N1-N0)/((D1-D0)/F)
