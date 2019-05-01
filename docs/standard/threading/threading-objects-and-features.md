---
title: İş parçacığı nesneleri ve özellikleri
ms.date: 10/01/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f25609bc3c4dd829c66a1a4514b7f1121f9c0909
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940939"
---
# <a name="threading-objects-and-features"></a>İş parçacığı nesneleri ve özellikleri

İle birlikte <xref:System.Threading.Thread?displayProperty=nameWithType> .NET sağlar sınıfını yardımcı sınıfları sayısı çok iş parçacıklı uygulamalar geliştirin. Aşağıdaki makaleler bu sınıflara genel bakış sunar:

|Başlık|Açıklama|  
|-----------|-----------------|  
|[Yönetilen iş parçacığı havuzu](the-managed-thread-pool.md)|Açıklar <xref:System.Threading.ThreadPool?displayProperty=nameWithType> .NET tarafından yönetilen çalışan iş parçacığı havuzu sağlar sınıfını.|  
|[Süreölçerler](timers.md)|Çok iş parçacıklı bir ortamda kullanılabilir .NET zamanlayıcılar açıklar.|
|[Eşitleme temellerine genel bakış](overview-of-synchronization-primitives.md)|Bir paylaşılan kaynağa veya denetimi iş parçacığı etkileşim erişimi eşitlemek için kullanılan türleri açıklanmaktadır.|
|[EventWaitHandle](eventwaithandle.md)|Açıklar <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> iş parçacığı eşitleme olayını temsil eden sınıf.|
|[CountdownEvent](countdownevent.md)|Açıklar <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> kendi sayısı sıfır olduğunda, ayarladığınız duruma bir iş parçacığı eşitleme olay temsil eden sınıf.|
|[Karşılıklı dışlamalar](mutexes.md)|Açıklar <xref:System.Threading.Mutex?displayProperty=nameWithType> , paylaşılan bir kaynağa özel erişim veren sınıf.|
|[Semaphore ve SemaphoreSlim](semaphore-and-semaphoreslim.md)|Açıklar <xref:System.Threading.Semaphore?displayProperty=nameWithType> sınıfını, paylaşılan bir kaynağa erişmek için iş parçacığı sayısı veya bir kaynak havuzu eşzamanlı olarak sınırlar.|
|[Engel](barrier.md)|Açıklar <xref:System.Threading.Barrier?displayProperty=nameWithType> sınıfını aşamalı işlemlerinde koordinasyon iş parçacıklarının engeli desenini uygular.|
|[SpinLock](spinlock.md)|Açıklar <xref:System.Threading.SpinLock?displayProperty=nameWithType> hafif bir yapısı için alternatif <xref:System.Threading.Monitor?displayProperty=nameWithType> belirli alt düzey kilitleme senaryoları için sınıf.|
|[SpinWait](spinwait.md)|Açıklar <xref:System.Threading.SpinWait?displayProperty=nameWithType> yapısı, döndürme tabanlı bekleme için destek sağlar.|

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
