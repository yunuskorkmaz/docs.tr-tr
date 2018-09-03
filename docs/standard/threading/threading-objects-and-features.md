---
title: İş parçacığı nesneleri ve özellikleri
ms.date: 08/16/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d56d962279120a03a6e4b89154ac1429ea5479e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43483664"
---
# <a name="threading-objects-and-features"></a>İş parçacığı nesneleri ve özellikleri

İle birlikte <xref:System.Threading.Thread?displayProperty=nameWithType> .NET sağlar sınıfını yardımcı sınıfları sayısı çok iş parçacıklı uygulamalar geliştirin. Aşağıdaki makaleler bu sınıflara genel bakış sunar:

|Başlık|Açıklama|  
|-----------|-----------------|  
|[Yönetilen iş parçacığı havuzu](the-managed-thread-pool.md)|Açıklar <xref:System.Threading.ThreadPool?displayProperty=nameWithType> .NET tarafından yönetilen çalışan iş parçacığı havuzu sağlar sınıfını.|  
|[Süreölçerler](timers.md)|Çok iş parçacıklı bir ortamda kullanılabilir zamanlayıcılar açıklar.|
|[Eşitleme temellerine genel bakış](overview-of-synchronization-primitives.md)|İş parçacığı etkileşim veri ya da Denetim erişimi eşitlemek için kullanılan sınıfları açıklar.|
|[EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)|Sinyal ve sinyalleri için bekleyen iş parçacığı etkinlikleri eşitlemek için kullanılan yönetilen bir olay bekleme tanıtıcıları açıklar.|
|[Karşılıklı dışlamalar](mutexes.md)|Nasıl kullanılacağını açıklayan bir <xref:System.Threading.Mutex?displayProperty=nameWithType> bir nesneye erişimi eşitleme ya da kendi eşitleme mekanizmaları oluşturun.|
|[Birbirine kenetlenmiş işlemler](interlocked-operations.md)|Açıklar <xref:System.Threading.Interlocked?displayProperty=nameWithType> birden çok iş parçacığı tarafından paylaşılan değişkenleri için atomik işlemler sağlar sınıfını.|
|[Okuyucu-Yazıcı Kilitleri](reader-writer-locks.md)|Açıklar <xref:System.Threading.ReaderWriterLockSlim?displayProperty=nameWithType> tek yazıcı/birden çok okuyucu semantikler sağlar sınıfını.|
|[Semaphore ve SemaphoreSlim](semaphore-and-semaphoreslim.md)|Açıklar <xref:System.Threading.Semaphore?displayProperty=nameWithType> sınıfı ve bu sınırlı kaynaklara erişimi denetlemek için nasıl kullanılacağını açıklar.|
|[Engel](barrier.md)|Açıklar <xref:System.Threading.Barrier?displayProperty=nameWithType> aşamalı işlemlerinde koordinasyon iş parçacıklarının engeli desenini uygulayan sınıf.|
|[SpinLock](spinlock.md)|Açıklar <xref:System.Threading.SpinLock?displayProperty=nameWithType> hafif bir sınıf için alternatif <xref:System.Threading.Monitor?displayProperty=nameWithType> alt düzey belirli senaryolar için sınıf.|
|[SpinWait](spinwait.md)|Açıklar <xref:System.Threading.SpinWait?displayProperty=nameWithType> çekirdek tabanlı bekleme başlatmadan önce meşgul dönme gerçekleştiren bir düşük düzeyli eşitleme temel sınıfı.|

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- [İş parçacığı kullanma ve iş parçacığı oluşturma](using-threads-and-threading.md)
- [Zaman Uyumsuz Dosya G/Ç](../io/asynchronous-file-i-o.md)
- [Paralel Programlama](../parallel-programming/index.md)
- [Görev Paralel Kitaplığı (TPL)](../parallel-programming/task-parallel-library-tpl.md)
