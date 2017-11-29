---
title: "Uç Noktası: Saniyede Güvenlik Doğrulaması ve Kimlik Doğrulaması Hatası"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89a70b90-d7e4-4b03-9b84-4dc88ce3d605
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: c6b50aa00fe59d0ad23d5ca0b77c7b89f97a0d1e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint-security-validation-and-authentication-failures-per-second"></a>Uç Noktası: Saniyede Güvenlik Doğrulaması ve Kimlik Doğrulaması Hatası
Sayaç adı: güvenlik doğrulaması ve kimlik doğrulama hataları saniye başına  
  
## <a name="description"></a>Açıklama  
 Bir ileti "Güvenlik çağrıları yetkilendirilmedi" sayacı tarafından kapsanmayan bir güvenlik sorunu nedeniyle reddedilen olduğunda bu sayaç artırılır. Bu tür sorunlar içerir:  
  
-   İstemci belirteci iletiden okunamıyor.  
  
-   İstemci belirteci kimlik doğrulaması (örneğin, hatalı parola) başarısız oldu.  
  
-   İmza doğrulaması başarısız oldu (örneğin, ileti değiştirilmiş).  
  
-   İleti yeniden yürütme saldırı sırasında gerçekleşebilir bir önceki bir yineleniyor.  
  
-   Bir şifre çözme hatası oluştu.  
  
-   Gereken bazı iletiden öğeleri (örneğin, eksik zaman damgası veya engelleme şifrelenmiş veriler) eksik.  
  
-   TLSNEGO/SPNEGO anlaşması sırasında hata oluştu.  
  
 Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır:  
  
 (N1-N0)/((D1-D0)/F)
