---
title: Yetkilendirilmeyen Güvenlik Çağrısı/Saniye
ms.date: 03/30/2017
ms.assetid: 0f189767-8c05-478a-8f0b-9228e5d351e5
ms.openlocfilehash: 8aed9f6b8c60c8aecd1b576c13a7063e3a492046
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552511"
---
# <a name="security-calls-not-authorized-per-second"></a>Yetkilendirilmeyen Güvenlik Çağrısı/Saniye
Sayaç adı: saniye başına yetkilendirilmemiş güvenlik çağrısı.  
  
## <a name="description"></a>Description  
 Bu işlemde yetkilendirilemeyen çağrı sayısı (saniye).  
  
 Bu sayaç, <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemin döndürdüğü zaman artırılır `false` . Gelen iletinin geçerli bir kullanıcıdan olduğunu ve düzgün şekilde korunduğunu gösterir, ancak kullanıcı belirli görevleri yapmak için yetkilendirilmemiş.  
  
 Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.  
  
 (N 1-N 0)/((D 1-D 0)/F)
