---
title: Saniyede Akışı Yapılan İşlem
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: 8b6077af3f98f7a205772b4883dc122374083e00
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163832"
---
# <a name="transactions-flowed-per-second"></a>Saniyede Akışı Yapılan İşlem
Sayaç adı: saniye başına akan Işlem  
  
## <a name="description"></a>Açıklama  
 Saniye içinde bu işleme aktarılan işlem sayısı. Bu sayaç, işleme gönderilen bir iletide bir işlem KIMLIĞI olduğunda artırılır.  
  
 Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.  
  
 (N 1-N 0)/((D 1-D 0)/F)
