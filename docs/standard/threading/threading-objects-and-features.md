---
title: İş parçacığı nesneleri ve özellikleri
ms.date: 10/01/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
ms.openlocfilehash: dd9b7b8cb194353d0a1c285af10d54dc7366896e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73128967"
---
# <a name="threading-objects-and-features"></a>İş parçacığı nesneleri ve özellikleri

<xref:System.Threading.Thread?displayProperty=nameWithType> .NET, sınıfla birlikte çok iş parçacığı uygulamaları geliştirmenize yardımcı olan bir dizi sınıf sağlar. Aşağıdaki makaleler bu sınıflara genel bakış sağlar:

|Başlık|Açıklama|  
|-----------|-----------------|  
|[Yönetilen iş parçacığı havuzu](the-managed-thread-pool.md)|.NET <xref:System.Threading.ThreadPool?displayProperty=nameWithType> tarafından yönetilen bir alt iş parçacığı havuzu sağlayan sınıfı açıklar.|  
|[Zamanlayıcılar](timers.md)|Çok iş parçacığı ortamında kullanılabilen .NET zamanlayıcılarını açıklar.|
|[Eşitleme temellerine genel bakış](overview-of-synchronization-primitives.md)|Paylaşılan bir kaynağa erişimi eşitlemek veya iş parçacığı etkileşimini denetlemek için kullanılabilecek türleri açıklar.|
|[EventWaitHandle](eventwaithandle.md)|İş <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> parçacığı eşitleme olayını temsil eden sınıfı açıklar.|
|[CountdownEvent](countdownevent.md)|Sayısı <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> sıfır olduğunda ayarlanan bir iş parçacığı eşitleme olayını temsil eden sınıfı açıklar.|
|[Karşılıklı dışlamalar](mutexes.md)|Paylaşılan <xref:System.Threading.Mutex?displayProperty=nameWithType> kaynağa özel erişim sağlayan sınıfı açıklar.|
|[Semafor ve SemaphoreSlim](semaphore-and-semaphoreslim.md)|Paylaşılan <xref:System.Threading.Semaphore?displayProperty=nameWithType> bir kaynağa veya aynı anda bir kaynak havuzuna erişebilen iş parçacığı sayısını sınırlayan sınıfı açıklar.|
|[Engel](barrier.md)|Aşamalı <xref:System.Threading.Barrier?displayProperty=nameWithType> işlemlerde iş parçacıklarının koordinasyonu için bariyer deseni uygulayan sınıfı açıklar.|
|[SpinLock](spinlock.md)|Belirli <xref:System.Threading.SpinLock?displayProperty=nameWithType> düşük düzeyli kilitleme senaryoları <xref:System.Threading.Monitor?displayProperty=nameWithType> için sınıfa hafif bir alternatif olan yapıyı açıklar.|
|[SpinWait](spinwait.md)|Spin <xref:System.Threading.SpinWait?displayProperty=nameWithType> tabanlı bekleme desteği sağlayan yapıyı açıklar.|

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- [İş parçacıkları ve iş parçacığı oluşturmayı kullanma](using-threads-and-threading.md)
- [Zaman Uyumsuz Dosya G/Ç](../io/asynchronous-file-i-o.md)
- [Paralel Programlama](../parallel-programming/index.md)
- [Görev Paralel Kitaplığı (TPL)](../parallel-programming/task-parallel-library-tpl.md)
