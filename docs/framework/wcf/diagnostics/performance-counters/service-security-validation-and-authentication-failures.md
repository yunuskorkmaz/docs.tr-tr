---
title: 'Hizmet: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hataları'
ms.date: 03/30/2017
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: e160b014b7aa7586566073b800084d44be15ccaf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474408"
---
# <a name="service-security-validation-and-authentication-failures"></a>Hizmet: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hataları
Sayaç adı: güvenlik doğrulaması ve kimlik doğrulama hataları  
  
## <a name="description"></a>Açıklama  
 Bir ileti "Güvenlik çağrıları yetkilendirilmedi" sayacı tarafından kapsanmayan bir güvenlik sorunu nedeniyle reddedilen olduğunda bu sayaç artırılır. Bu tür sorunlar içerir:  
  
-   İstemci belirteci iletiden okunamıyor.  
  
-   İstemci belirteci kimlik doğrulaması (örneğin, hatalı parola) başarısız oldu.  
  
-   İmza doğrulaması başarısız oldu (örneğin, ileti değiştirilmiş).  
  
-   İleti yeniden yürütme saldırı sırasında gerçekleşebilir bir önceki bir yineleniyor.  
  
-   Bir şifre çözme hatası oluştu.  
  
-   Gereken bazı iletiden öğeleri (örneğin, eksik zaman damgası veya engelleme şifrelenmiş veriler) eksik.  
  
-   TLSNEGO/SPNEGO anlaşması sırasında hata oluştu.
