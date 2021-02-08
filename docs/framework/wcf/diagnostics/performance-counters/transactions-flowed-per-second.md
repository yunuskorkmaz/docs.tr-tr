---
description: 'Hakkında daha fazla bilgi edinin: saniye başına aktarılan Işlem'
title: Saniyede Akışı Yapılan İşlem
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: f37c79e89efb8a013719f44350772919b7222a61
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771008"
---
# <a name="transactions-flowed-per-second"></a>Saniyede Akışı Yapılan İşlem

Sayaç adı: saniye başına akan Işlem  
  
## <a name="description"></a>Description  

 Saniye içinde bu işleme aktarılan işlem sayısı. Bu sayaç, işleme gönderilen bir iletide bir işlem KIMLIĞI olduğunda artırılır.  
  
 Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.  
  
 (N 1-N 0)/((D 1-D 0)/F)
