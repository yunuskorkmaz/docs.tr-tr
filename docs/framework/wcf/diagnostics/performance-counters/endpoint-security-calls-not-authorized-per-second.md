---
title: 'Uç Noktası: Saniyede Yetkisiz Güvenlik Çağrısı'
ms.date: 03/30/2017
ms.assetid: c8a1547b-986b-45c1-b302-dea0cd4b516d
author: BrucePerlerMS
ms.openlocfilehash: 4abea795eb196d339beec17fa7a171927aa85324
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47194067"
---
# <a name="endpoint-security-calls-not-authorized-per-second"></a>Uç Noktası: Saniyede Yetkisiz Güvenlik Çağrısı
Sayaç adı: Saniyede yetkisiz güvenlik çağrısı.  
  
## <a name="description"></a>Açıklama  
 Geçerli bir kullanıcıdan ve düzgün şekilde korumalı saniyenin, ancak kullanıcı gelen ileti sayısı, belirli görevler gerçekleştirmek için yetkili değil.  
  
 Bu sayaç artırılır, <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemi döndürür `false`.  
  
 Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır.  
  
 (1 - N 0 N) / ((D 1 - D 0) / F)
