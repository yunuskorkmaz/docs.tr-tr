---
title: Saniyede Akışı Yapılan İşlem
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: b47219bd58a9b6c4401baa73177928ddca5b6a8b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254148"
---
# <a name="transactions-flowed-per-second"></a>Saniyede Akışı Yapılan İşlem

Sayaç adı: saniye başına akan Işlem  
  
## <a name="description"></a>Açıklama  

 Saniye içinde bu işleme aktarılan işlem sayısı. Bu sayaç, işleme gönderilen bir iletide bir işlem KIMLIĞI olduğunda artırılır.  
  
 Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.  
  
 (N 1-N 0)/((D 1-D 0)/F)
