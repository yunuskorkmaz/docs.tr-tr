---
title: 'Uç noktası: Saniyede Akışı Yapılan İşlem'
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: 39458dcb6ac033fd5084b5f2e760e0e26c345da7
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163559"
---
# <a name="endpoint-transactions-flowed-per-second"></a>Uç noktası: Saniyede Akışı Yapılan İşlem
Sayaç adı: saniye başına akan Işlem.  
  
## <a name="description"></a>Açıklama  
 Bu bitiş noktasındaki işlemlere aktarılan işlem sayısı (saniye). Bu sayaç, uç noktaya gönderilen bir iletide bir işlem KIMLIĞI olduğunda artırılır.  
  
 Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.  
  
 (N 1-N 0)/((D 1-D 0)/F)
