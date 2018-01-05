---
title: "Uç Noktası: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hataları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5bad60aa-6084-4c7b-aefd-9b581f04382e
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 5bd38ae0e3506397378b7c59976c6c692045054d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="endpoint-security-validation-and-authentication-failures"></a>Uç Noktası: Güvenlik Doğrulaması ve Kimlik Doğrulaması Hataları
Sayaç adı: güvenlik doğrulaması ve kimlik doğrulama hataları  
  
## <a name="description"></a>Açıklama  
 Bir ileti "Güvenlik çağrıları yetkilendirilmedi" sayacı tarafından kapsanmayan bir güvenlik sorunu nedeniyle reddedilen olduğunda bu sayaç artırılır. Bu tür sorunlar içerir:  
  
-   İstemci belirteci iletiden okunamıyor.  
  
-   İstemci belirteci kimlik doğrulaması (hatalı parola) başarısız oldu.  
  
-   İmza doğrulaması başarısız oldu (ileti oynanmış).  
  
-   İleti yeniden yürütme saldırı sırasında gerçekleşebilir bir önceki bir yineleniyor.  
  
-   Bir şifre çözme hatası oluştu.  
  
-   Gelen iletiyi (zaman damgası veya şifrelenmiş veri bloğunu eksik) bazı gerekli öğeleri eksik.  
  
-   TLSNEGO/SPNEGO anlaşması sırasında hata oluştu.
