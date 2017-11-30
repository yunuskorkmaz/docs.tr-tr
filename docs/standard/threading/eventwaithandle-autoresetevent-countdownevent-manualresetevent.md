---
title: EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wait handles
- threading [.NET Framework], EventWaitHandle class
- event wait handles [.NET Framework]
ms.assetid: cd94fc34-ac15-427f-b723-a1240a4fab7d
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5c0bcb27ed9c8981665a50c129dfbd824c9612f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="eventwaithandle-autoresetevent-countdownevent-manualresetevent"></a>EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent
Olay bekleme tanıtıcıları etkinlikleri birbirine sinyal ve birbirlerinin sinyalleri bekleyen eşitlemek için iş parçacığı izin verir. Bu eşitleme olaylar üzerinde Win32 bekleme tanıtıcıları tabanlı ve iki türlerine ayrılabilir: da otomatik olarak işaret sıfırlanır ve da el ile sıfırlayın.  
  
 Olay bekleme tanıtıcıları, birçok aynı eşitleme senaryolarda kullanışlıdır <xref:System.Threading.Monitor> sınıfı. Olay bekleme tanıtıcıları daha kolay genellikle <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> ve <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> yöntemleri ve sinyal üzerinde daha fazla denetim sağlar. İzleyicileri uygulama etki alanı için yerel ise adlandırılmış olay bekleme tanıtıcıları etkinlikleri uygulama etki alanları ve işlemler arasında eşitlemek için de kullanılabilir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md)  
 <xref:System.Threading.EventWaitHandle> Sınıfı temsil edebilen ya da otomatik veya el ile sıfırlama olayları ve yerel ya da olaylar veya sistem olayları adlı.  
  
 [AutoResetEvent](../../../docs/standard/threading/autoresetevent.md)  
 <xref:System.Threading.AutoResetEvent> Sınıfı türer <xref:System.Threading.EventWaitHandle> ve otomatik olarak sıfırlar yerel bir olayı temsil eder.  
  
 [ManualResetEvent ve ManualResetEventSlim](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md)  
 <xref:System.Threading.ManualResetEvent> Sınıfı türer <xref:System.Threading.EventWaitHandle> ve el ile sıfırlamanız gerekir yerel bir olayı temsil eder. <xref:System.Threading.ManualResetEventSlim> Aynı işlem içindeki olaylar için kullanılan basit ve hızlı bir sürüm bir sınıftır.  
  
 [CountdownEvent](../../../docs/standard/threading/countdownevent.md)  
 <xref:System.Threading.CountdownEvent> Sınıfı kullanır bekleme tanıtıcıları kodda çatalı/JOIN paralellik desenlerini uygulama için basitleştirilmiş bir yol sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Bekleme tanıtıcıları](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 <xref:System.Threading.WaitHandle> Sınıf için temel sınıfı olan <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.Semaphore>, ve <xref:System.Threading.Mutex> sınıfları. Statik yöntemler gibi içeren <xref:System.Threading.WaitHandle.SignalAndWait%2A> ve <xref:System.Threading.WaitHandle.WaitAll%2A> bekleme tanıtıcıları tüm türleri ile çalışırken yararlı olan.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 [İş parçacığı nesneleri ve özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)  
 [Yönetilen iş parçacığı oluşturma temelleri](../../../docs/standard/threading/managed-threading-basics.md)
