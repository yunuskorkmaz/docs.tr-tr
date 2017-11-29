---
title: "Güvenlik Doğrulaması ve Kimlik Doğrulaması Hataları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d4e3666-dfc6-421c-baf8-9479c22f7050
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: c1d448d709c7ad20e9d08a291f5a38546cd93ce4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="security-validation-and-authentication-failures"></a>Güvenlik Doğrulaması ve Kimlik Doğrulaması Hataları
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
