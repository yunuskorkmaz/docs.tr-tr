---
title: 'Uç Noktası: Saniyede Yetkisiz Güvenlik Çağrısı'
ms.date: 03/30/2017
ms.assetid: c8a1547b-986b-45c1-b302-dea0cd4b516d
ms.openlocfilehash: 4925a0a53b03b061561aab396377012acd130797
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90549702"
---
# <a name="endpoint-security-calls-not-authorized-per-second"></a>Uç Noktası: Saniyede Yetkisiz Güvenlik Çağrısı
Sayaç adı: saniye başına yetkilendirilmemiş güvenlik çağrısı.  
  
## <a name="description"></a>Description  
 Saniye içinde geçerli bir kullanıcıdan gelen ve düzgün şekilde korunan gelen ileti sayısı, ancak kullanıcı belirli görevleri yapmak için yetkilendirilmemiş.  
  
 Bu sayaç, <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemin döndürdüğü zaman artırılır `false` .  
  
 Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.  
  
 (N 1-N 0)/((D 1-D 0)/F)
