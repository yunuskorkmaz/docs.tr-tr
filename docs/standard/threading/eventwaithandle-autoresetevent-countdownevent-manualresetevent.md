---
title: EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- wait handles
- threading [.NET Framework], EventWaitHandle class
- event wait handles [.NET Framework]
ms.assetid: cd94fc34-ac15-427f-b723-a1240a4fab7d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f818ecf52ae1179d6d32d0b76cea3cc2a8f36ea8
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43416418"
---
# <a name="eventwaithandle-autoresetevent-countdownevent-manualresetevent"></a>EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent
Olay bekleme tanıtıcıları birbirine sinyal ve birbirlerinin sinyalleri bekleyen etkinlikleri eşitlemek için iş parçacığı izin verir. Bu eşitleme olayları Win32 bekleme tanıtıcıları üzerinde temel alır ve iki tür olarak ayrılabilir: sinyal olduğunda otomatik olarak sıfırlayan ve el ile Sıfırlanan.  
  
 Olay bekleme tanıtıcıları, birçok aynı eşitleme senaryolarda kullanışlıdır <xref:System.Threading.Monitor> sınıfı. Olay bekleme tanıtıcıları daha kolay genellikle <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> ve <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> yöntemleri ve sinyal üzerinde daha fazla denetim sağlar. İzleyicileri uygulama etki alanı için yerel ise adlandırılmış olay bekleme tanıtıcıları uygulama etki alanları ve işlemleri arasında etkinlikleri eşitlemek için de kullanılabilir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md)  
 <xref:System.Threading.EventWaitHandle> Veya el ile sıfırlama olayları ve yerel ya da olaylar veya sistem olaylarını adlı sınıfı ya da otomatik temsil eder.  
  
 [AutoResetEvent](../../../docs/standard/threading/autoresetevent.md)  
 <xref:System.Threading.AutoResetEvent> Sınıf türetilir <xref:System.Threading.EventWaitHandle> ve otomatik olarak sıfırlar yerel bir olayı temsil eder.  
  
 [ManualResetEvent ve ManualResetEventSlim](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md)  
 <xref:System.Threading.ManualResetEvent> Sınıf türetilir <xref:System.Threading.EventWaitHandle> ve el ile sıfırlamanız gerekir yerel bir olayı temsil eder. <xref:System.Threading.ManualResetEventSlim> Sınıfı, aynı işlem içinde olaylar için kullanılan basit ve hızlı bir sürümü.  
  
 [CountdownEvent](../../../docs/standard/threading/countdownevent.md)  
 <xref:System.Threading.CountdownEvent> Sınıfı çatal/birleştir paralellik desenleri bekleme tanıtıcıları kullanan koda uygulanması için basitleştirilmiş bir yol sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Bekleme tanıtıcıları](https://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 <xref:System.Threading.WaitHandle> İçin temel sınıfı <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.Semaphore>, ve <xref:System.Threading.Mutex> sınıfları. Statik yöntemler gibi içeren <xref:System.Threading.WaitHandle.SignalAndWait%2A> ve <xref:System.Threading.WaitHandle.WaitAll%2A> bekleme tanıtıcıları tüm türleriyle çalışırken yararlı olan.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 [İş Parçacığı Nesneleri ve Özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)  
 [Yönetilen İş Parçacığı Oluşturma Temelleri](../../../docs/standard/threading/managed-threading-basics.md)
