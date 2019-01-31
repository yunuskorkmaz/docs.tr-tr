---
title: EventWaitHandle, CountdownEvent
ms.date: 09/14/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- wait handles
- threading [.NET Framework], EventWaitHandle class
- event wait handles [.NET Framework]
ms.assetid: cd94fc34-ac15-427f-b723-a1240a4fab7d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fafdc2a360038021217d9a42406c971b1094678b
ms.sourcegitcommit: dcc8feeff4718664087747529638ec9b47e65234
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/31/2019
ms.locfileid: "55479938"
---
# <a name="eventwaithandle-countdownevent"></a>EventWaitHandle, CountdownEvent

Olay bekleme tanıtıcıları birbirine sinyal ve birbirlerinin sinyalleri bekleyen etkinlikleri eşitlemek için iş parçacığı izin verir. Bu eşitleme olaylar üzerinde işletim sistemi bekleme tanıtıcıları temel alır ve iki tür olarak ayrılabilir: sinyal olduğunda otomatik olarak sıfırlayan ve el ile Sıfırlanan.  
  
Olay bekleme tanıtıcıları, birçok aynı eşitleme senaryolarda kullanışlıdır <xref:System.Threading.Monitor> sınıfı. Olay bekleme tanıtıcıları daha kolay genellikle <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> ve <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> yöntemleri ve sinyal üzerinde daha fazla denetim sağlar. İzleyicileri uygulama etki alanı için yerel ise adlandırılmış olay bekleme tanıtıcıları uygulama etki alanları ve işlemleri arasında etkinlikleri eşitlemek için de kullanılabilir.  
  
## <a name="in-this-section"></a>Bu bölümde

 [EventWaitHandle](eventwaithandle.md)  
 <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> Veya el ile sıfırlama olayları ve yerel ya da olaylar veya sistem olaylarını adlı sınıfı ya da otomatik temsil eder.  
  
 [CountdownEvent](countdownevent.md)  
 <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> Sınıfı çatal/birleştir paralellik desenleri bekleme tanıtıcıları kullanan koda uygulanması için basitleştirilmiş bir yol sağlar.  

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.Threading.Barrier?displayProperty=nameWithType>
- [İş parçacığı nesneleri ve özellikleri](threading-objects-and-features.md)
- [Yönetilen iş parçacığı oluşturma temelleri](managed-threading-basics.md)
