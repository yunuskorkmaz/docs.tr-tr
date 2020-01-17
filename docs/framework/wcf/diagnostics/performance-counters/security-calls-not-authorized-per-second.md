---
title: Yetkilendirilmeyen Güvenlik Çağrısı/Saniye
ms.date: 03/30/2017
ms.assetid: 0f189767-8c05-478a-8f0b-9228e5d351e5
ms.openlocfilehash: 2986ba241ef9b6c110a4742f77320469cdf5f07a
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163936"
---
# <a name="security-calls-not-authorized-per-second"></a>Yetkilendirilmeyen Güvenlik Çağrısı/Saniye
Sayaç adı: saniye başına yetkilendirilmemiş güvenlik çağrısı.  
  
## <a name="description"></a>Açıklama  
 Bu işlemde yetkilendirilemeyen çağrı sayısı (saniye).  
  
 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemi `false`döndürdüğünde Bu sayaç artırılır. Gelen iletinin geçerli bir kullanıcıdan olduğunu ve düzgün şekilde korunduğunu gösterir, ancak kullanıcı belirli görevleri yapmak için yetkilendirilmemiş.  
  
 Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.  
  
 (N 1-N 0)/((D 1-D 0)/F)
