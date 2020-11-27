---
title: 'Hizmet: Saniye Başına Çağrı'
ms.date: 03/30/2017
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
ms.openlocfilehash: 7e702d402909c4a85a2cb42c837e0813c4d9f841
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96252887"
---
# <a name="service-calls-per-second"></a>Hizmet: Saniye Başına Çağrı

Sayaç adı: saniye başına çağrı.  
  
## <a name="description"></a>Açıklama  

 Bu hizmete saniye içinde yapılan çağrı sayısı.  
  
 Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.  
  
 (N 1-N 0)/((D 1-D 0)/F) pay (N) son örnekleme aralığı sırasında gerçekleştirilen işlem sayısını temsil ediyorsa, payda (D) son örnekleme aralığı sırasında geçen işaret sayısını temsil eder ve F, Tick 'lerin sıklığıdır.
