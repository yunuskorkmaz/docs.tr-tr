---
title: İş parçacığı nesneleri ve özellikleri
ms.date: 10/01/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
ms.openlocfilehash: dd9b7b8cb194353d0a1c285af10d54dc7366896e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128967"
---
# <a name="threading-objects-and-features"></a>İş parçacığı nesneleri ve özellikleri

.NET <xref:System.Threading.Thread?displayProperty=nameWithType> sınıfıyla birlikte çok iş parçacıklı uygulamalar geliştirmenize yardımcı olan bir dizi sınıf sağlar. Aşağıdaki makaleler, bu sınıflara genel bakış sağlar:

|Başlık|Açıklama|  
|-----------|-----------------|  
|[Yönetilen iş parçacığı havuzu](the-managed-thread-pool.md)|.NET tarafından yönetilen bir çalışan iş parçacığı havuzu sağlayan <xref:System.Threading.ThreadPool?displayProperty=nameWithType> sınıfını açıklar.|  
|[Süreölçerler](timers.md)|Çoklu iş parçacıklı bir ortamda kullanılabilen .NET zamanlayıcıları açıklanmaktadır.|
|[Eşitleme temelleri 'ne genel bakış](overview-of-synchronization-primitives.md)|Paylaşılan bir kaynağa veya denetim iş parçacığı etkileşimine erişimi eşzamanlı hale getirmek için kullanılabilecek türleri açıklar.|
|[EventWaitHandle](eventwaithandle.md)|Bir iş parçacığı eşitleme olayını temsil eden <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> sınıfını açıklar.|
|[CountdownEvent](countdownevent.md)|Sayısı sıfır olduğunda ayarlanan bir iş parçacığı eşitleme olayını temsil eden <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> sınıfını açıklar.|
|[Karşılıklı dışlamalar](mutexes.md)|Paylaşılan bir kaynağa özel erişim veren <xref:System.Threading.Mutex?displayProperty=nameWithType> sınıfını açıklar.|
|[Semaphore ve SemaphoreSlim](semaphore-and-semaphoreslim.md)|Paylaşılan bir kaynağa veya bir kaynak havuzuna eşzamanlı olarak erişebilen iş parçacığı sayısını sınırlayan <xref:System.Threading.Semaphore?displayProperty=nameWithType> sınıfını açıklar.|
|[Engel](barrier.md)|Aşamalı işlemlerde iş parçacıklarının koordinasyonu için engel modelini uygulayan <xref:System.Threading.Barrier?displayProperty=nameWithType> sınıfını açıklar.|
|[SpinLock](spinlock.md)|Bazı düşük düzey kilitleme senaryoları için <xref:System.Threading.Monitor?displayProperty=nameWithType> sınıfına hafif bir alternatif olan <xref:System.Threading.SpinLock?displayProperty=nameWithType> yapısını açıklar.|
|[SpinWait](spinwait.md)|, Döndürme tabanlı bekleme desteği sağlayan <xref:System.Threading.SpinWait?displayProperty=nameWithType> yapısını açıklar.|

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- [İş parçacıkları ve iş parçacığı kullanma](using-threads-and-threading.md)
- [Zaman Uyumsuz Dosya G/Ç](../io/asynchronous-file-i-o.md)
- [Paralel Programlama](../parallel-programming/index.md)
- [Görev Paralel Kitaplığı (TPL)](../parallel-programming/task-parallel-library-tpl.md)
