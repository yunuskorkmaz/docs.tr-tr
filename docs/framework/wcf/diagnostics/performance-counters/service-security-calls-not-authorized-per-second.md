---
title: 'Hizmet: Saniyede Yetkisiz Güvenlik Çağrısı'
ms.date: 03/30/2017
ms.assetid: 1eeade5a-ea62-4757-b1f9-1b1b1746abd1
ms.openlocfilehash: db9e333f740f19e4f82ea0f1306a11e6c21ba996
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236929"
---
# <a name="service-security-calls-not-authorized-per-second"></a>Hizmet: Saniyede Yetkisiz Güvenlik Çağrısı

Sayaç adı: saniye başına yetkilendirilmemiş güvenlik çağrısı  
  
## <a name="description"></a>Açıklama  

 Bir saniye içinde, geçerli bir kullanıcıdan gelen ve düzgün şekilde korunan, ancak kullanıcı belirli görevleri yapmak için yetkilendirilmemiş olan gelen ileti sayısı.  
  
 Bu sayaç, <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemin döndürdüğü zaman artırılır `false` .  
  
 Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.  
  
 (N 1-N 0)/((D 1-D 0)/F)
