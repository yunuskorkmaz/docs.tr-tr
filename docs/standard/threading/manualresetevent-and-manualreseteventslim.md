---
title: ManualResetEvent ve ManualResetEventSlim
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], ManualResetEvent class
- ManualResetEvent class, about ManualResetEvent class
ms.assetid: 465fdcf9-ba24-4d8d-a43f-d983b7cb0cc6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4a6950d17fef60298a2e47b63bec068554b2b8b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43557655"
---
# <a name="manualresetevent-and-manualreseteventslim"></a>ManualResetEvent ve ManualResetEventSlim
<xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> Sınıf işareti verilen sonra el ile sıfırlamanız gerekir bir yerel bekleme tanıtıcısı olayı temsil eder. Bu sınıfın temel sınıfının, özel bir durum temsil <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>. Bkz: [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) el ile özellikleri ve kullanmak için kavramsal belgelerde olayların sıfırlayın.  
  
 A <xref:System.Threading.ManualResetEvent> nesne kadar sinyal kalır, <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> yöntemi çağrılır. Nesnenin durumu sinyal sırada iş parçacığı veya bu sinyal sonra olay beklemek iş parçacığı beklenirken, herhangi bir sayı serbest bırakılabilir. <xref:System.Threading.ManualResetEvent> Win32 öğesine karşılık gelen `CreateEvent` belirleme çağrısında `true` için `bManualReset` bağımsız değişken.  
  
 İçinde [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], kullanabileceğiniz <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> bekleme süresini çok kısa olması beklenir ve olay, bir işlem sınırını aşan değil zamanı daha iyi performans için sınıf. <xref:System.Threading.ManualResetEventSlim> Olayın sinyal haline beklerken kısa bir süre için dönen meşgul kullanır. Bekleme süresini kısa olduğunda dönme beklemeden çok daha düşük maliyetli bekleme tanıtıcıları kullanılarak olabilir. Ancak, olay belirli bir zaman döneminde sinyal haline değil <xref:System.Threading.ManualResetEventSlim> resorts normal olay işleyici bekleyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş parçacığı oluşturma](../../../docs/standard/threading/index.md)  
 [İş Parçacığı Nesneleri ve Özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)  
 [Bekleme tanıtıcıları](https://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 [AutoResetEvent](../../../docs/standard/threading/autoresetevent.md)  
 [SpinWait](../../../docs/standard/threading/spinwait.md)  
 [Semaphore ve SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)
