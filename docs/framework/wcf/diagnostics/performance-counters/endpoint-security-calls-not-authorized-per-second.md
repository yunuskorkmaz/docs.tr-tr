---
title: 'Uç noktası: Yetkilendirilmeyen Güvenlik Çağrısı/Saniye'
ms.date: 03/30/2017
ms.assetid: c8a1547b-986b-45c1-b302-dea0cd4b516d
ms.openlocfilehash: c62bec570daf8b107ca0540871eb6eac43ca2d7e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61951120"
---
# <a name="endpoint-security-calls-not-authorized-per-second"></a>Uç noktası: Yetkilendirilmeyen Güvenlik Çağrısı/Saniye
Sayaç adı: Saniyede yetkilendirilmeyen güvenlik çağrıları.  
  
## <a name="description"></a>Açıklama  
 Geçerli bir kullanıcıdan ve düzgün şekilde korumalı saniyenin, ancak kullanıcı gelen ileti sayısı, belirli görevler gerçekleştirmek için yetkili değil.  
  
 Bu sayaç artırılır, <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemi döndürür `false`.  
  
 Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır.  
  
 (1 - N 0 N) / ((D 1 - D 0) / F)
