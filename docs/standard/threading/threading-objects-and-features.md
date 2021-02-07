---
description: 'Hakkında daha fazla bilgi edinin: Iş parçacığı nesneleri ve özellikleri'
title: İş parçacığı nesneleri ve özellikleri
ms.date: 10/01/2018
helpviewer_keywords:
- threading [.NET], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
ms.openlocfilehash: 7e8167c42780ccc70c37a10bbb3a65483efabb24
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675422"
---
# <a name="threading-objects-and-features"></a>İş parçacığı nesneleri ve özellikleri

<xref:System.Threading.Thread?displayProperty=nameWithType>.NET sınıfı ile birlikte, çok iş parçacıklı uygulamalar geliştirmenize yardımcı olacak bir dizi sınıf sağlar. Aşağıdaki makaleler, bu sınıflara genel bakış sağlar:

|Başlık|Açıklama|  
|-----------|-----------------|  
|[Yönetilen iş parçacığı havuzu](the-managed-thread-pool.md)|<xref:System.Threading.ThreadPool?displayProperty=nameWithType>.NET tarafından yönetilen bir çalışan iş parçacığı havuzu sağlayan sınıfını açıklar.|  
|[Zamanlayıcılar](timers.md)|Çoklu iş parçacıklı bir ortamda kullanılabilen .NET zamanlayıcıları açıklanmaktadır.|
|[Eşitleme temellerine genel bakış](overview-of-synchronization-primitives.md)|Paylaşılan bir kaynağa veya denetim iş parçacığı etkileşimine erişimi eşzamanlı hale getirmek için kullanılabilecek türleri açıklar.|
|[EventWaitHandle](eventwaithandle.md)|<xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>İş parçacığı eşitleme olayını temsil eden sınıfını açıklar.|
|[CountdownEvent](countdownevent.md)|<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>Sayısı sıfır olduğunda ayarlanmış bir iş parçacığı eşitleme olayını temsil eden sınıfını açıklar.|
|[Zaman Uyumu Sağlayıcılar](mutexes.md)|<xref:System.Threading.Mutex?displayProperty=nameWithType>Paylaşılan bir kaynağa özel erişim veren sınıfını açıklar.|
|[Semafor ve SemaphoreSlim](semaphore-and-semaphoreslim.md)|<xref:System.Threading.Semaphore?displayProperty=nameWithType>Paylaşılan bir kaynağa veya bir kaynak havuzuna eşzamanlı olarak erişebilen iş parçacığı sayısını sınırlayan sınıfı açıklar.|
|[Engel](barrier.md)|<xref:System.Threading.Barrier?displayProperty=nameWithType>Aşamalı işlemlerde iş parçacıklarının koordinasyonu için engel modelini uygulayan sınıfını açıklar.|
|[SpinLock](spinlock.md)|<xref:System.Threading.SpinLock?displayProperty=nameWithType> <xref:System.Threading.Monitor?displayProperty=nameWithType> Belirli alt düzey kilitleme senaryolarında sınıfına hafif bir alternatif olan yapıyı açıklar.|
|[SpinWait](spinwait.md)|<xref:System.Threading.SpinWait?displayProperty=nameWithType>, Döndürme tabanlı bekleme desteği sağlayan yapıyı açıklar.|

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- [İş parçacıkları ve iş parçacığı oluşturmayı kullanma](using-threads-and-threading.md)
- [Zaman uyumsuz dosya g/ç](../io/asynchronous-file-i-o.md)
- [Paralel programlama](../parallel-programming/index.md)
- [Görev Paralel Kitaplığı (TPL)](../parallel-programming/task-parallel-library-tpl.md)
