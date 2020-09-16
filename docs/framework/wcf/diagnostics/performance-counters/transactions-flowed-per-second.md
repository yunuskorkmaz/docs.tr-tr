---
title: Saniyede Akışı Yapılan İşlem
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: d55856a5d820df2c668863a2a3e853995a113143
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552212"
---
# <a name="transactions-flowed-per-second"></a>Saniyede Akışı Yapılan İşlem
Sayaç adı: saniye başına akan Işlem  
  
## <a name="description"></a>Description  
 Saniye içinde bu işleme aktarılan işlem sayısı. Bu sayaç, işleme gönderilen bir iletide bir işlem KIMLIĞI olduğunda artırılır.  
  
 Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.  
  
 (N 1-N 0)/((D 1-D 0)/F)
