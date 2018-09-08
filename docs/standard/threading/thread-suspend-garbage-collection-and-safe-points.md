---
title: Thread.Suspend Çöp Toplama ve Güvenli Noktalar
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- suspending threads
- safe points
- threading [.NET Framework], suspending
- threading [.NET Framework], garbage collection
- garbage collection, threads
ms.assetid: e8f58e17-2714-4821-802a-f8eb3b2baa62
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fc3af01167fe97b701bdb0c7bc37af02d8e8a77c
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44130860"
---
# <a name="threadsuspend-garbage-collection-and-safe-points"></a>Thread.Suspend Çöp Toplama ve Güvenli Noktalar
Çağırdığınızda <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> bir iş parçacığında, bir iş parçacığını askıya alma isteğinde bulundu ve güvenli bir noktadan aslında bir iş parçacığını askıya almadan önce ulaştı kadar yürütmek iş parçacığının sağlar sistem notlar. Bir güvenli iş parçacığı hangi çöp toplama gerçekleştirilebilir, yürütme noktasında noktasıdır.  
  
 Güvenli bir noktasına ulaşıldığında, çalışma zamanı askıya alınan iş parçacığı yönetilen kodda herhangi bir gelişme yapmaz garanti eder. Her zaman dışında yönetilen bir kodu yürüten bir iş parçacığı çöp toplama işlemi için güvenli ve yönetilen kodun yürütülmesini sürdürmek deneme kadar yürütülmeye devam eder.  
  
> [!NOTE]
>  Bir atık toplama işlemi gerçekleştirmek için çalışma zamanı dışında koleksiyonu gerçekleştiren iş parçacığının tüm iş parçacıkları askıya gerekir. Askıya alınmadan önce her bir iş parçacığı güvenli bir noktaya sunulmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Thread>  
- <xref:System.GC>  
- [İş parçacığı oluşturma](../../../docs/standard/threading/index.md)  
- [Otomatik Bellek Yönetimi](../../../docs/standard/automatic-memory-management.md)
