---
title: "Thread.Suspend Çöp Toplama ve Güvenli Noktalar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- suspending threads
- safe points
- threading [.NET Framework], suspending
- threading [.NET Framework], garbage collection
- garbage collection, threads
ms.assetid: e8f58e17-2714-4821-802a-f8eb3b2baa62
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e47674ef8d1b1a7487e42765bcbce4b33cf98769
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="threadsuspend-garbage-collection-and-safe-points"></a>Thread.Suspend Çöp Toplama ve Güvenli Noktalar
Çağırdığınızda <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> bir iş parçacığında, bir iş parçacığı askıya istendi ve güvenli bir noktası iş parçacığı gerçekten askıya almadan önce ulaştı kadar yürütmek iş parçacığı verir sistem notlar. Bir güvenli iş parçacığı yürütmesi sırasında hangi atık toplama gerçekleştirilebilir noktasında noktasıdır.  
  
 Çalışma zamanı güvenli bir noktaya ulaşıldığında, askıya alınmış iş parçacığı yönetilen kodda herhangi gelişme yapmaz güvence altına alır. Her zaman dışında yönetilen kod parçacığı atık toplama için güvenli ve yönetilen kodun yürütülmesini sürdürmek deneme kadar yürütülmeye devam eder.  
  
> [!NOTE]
>  Çöp toplama gerçekleştirmek için çalışma zamanı koleksiyonu gerçekleştiren iş parçacığı dışında tüm iş parçacıklarını askıya alma gerekir. Askıya alınmadan önce her bir iş parçacığı güvenli noktasına duruma getirilmesi gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.Thread>  
 <xref:System.GC>  
 [İş parçacığı oluşturma](../../../docs/standard/threading/index.md)  
 [Otomatik bellek yönetimi](../../../docs/standard/automatic-memory-management.md)
