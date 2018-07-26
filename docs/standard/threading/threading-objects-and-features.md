---
title: İş Parçacığı Nesneleri ve Özellikleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d689aeb91ad79b776c3b93c1809ec46947ea60b
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874793"
---
# <a name="threading-objects-and-features"></a>İş Parçacığı Nesneleri ve Özellikleri
.NET Framework yardımcı nesnelerin sayısını sağlar. birden çok iş parçacıklı uygulamaları oluşturmak ve yönetmek. Yönetilen iş parçacıkları tarafından temsil edilir <xref:System.Threading.Thread> sınıfı. <xref:System.Threading.ThreadPool> Kolay oluşturulması ve yönetimi, çok iş parçacıklı arka plan görevlerinin sınıfı sağlar. <xref:System.ComponentModel.BackgroundWorker> Sınıfla aynı kullanıcı arabirimi ile etkileşim görevler için. <xref:System.Threading.Timer> Sınıfı zaman aralıklarında arka plan görevleri yürütür.  
  
 Ayrıca, bir dizi etkinlikler dahil olmak üzere iş parçacığı, eşitleme sınıfları vardır <xref:System.Threading.Semaphore> ve <xref:System.Threading.EventWaitHandle> .NET Framework 2.0 sürümünde sunulan sınıfları. İçinde bu sınıflarının özellikleri karşılaştırılır [eşitleme temellerine genel bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Yönetilen İş Parçacığı Havuzu](../../../docs/standard/threading/the-managed-thread-pool.md)  
 Açıklar **iş parçacığı havuzu** herhangi bir iş parçacığı yönetim kendiniz yapmak zorunda kalmadan bir görev yürütmek için bir iş parçacığı istemenizi sağlar sınıfını.  
  
 [Süreölçerler](../../../docs/standard/threading/timers.md)  
 Çok iş parçacıklı bir ortamda kullanılabilir zamanlayıcılar açıklar.  
  
 [İzleyiciler](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 Nasıl kullanılacağını açıklar **İzleyici** sınıf üyesi erişimi eşitlemek için veya kendi iş parçacığı yönetimi türleri oluşturmak için.  
  
 [Bekleme tanıtıcıları](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 Açıklar <xref:System.Threading.WaitHandle> sınıfı, olay yönelik soyut temel sınıf bekleme tanıtıcıları, mutex'leri ve birden çok eşitleme olay beklemek sağlayan semaforları.  
  
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 Sinyal ve sinyalleri için bekleyen iş parçacığı etkinlikleri eşitlemek için kullanılan yönetilen bir olay bekleme tanıtıcıları açıklar.  
  
 [Karşılıklı dışlamalar](../../../docs/standard/threading/mutexes.md)  
 Nasıl kullanılacağını açıklayan bir <xref:System.Threading.Mutex> bir nesneye erişimi eşitleme ya da kendi eşitleme mekanizmaları oluşturun.  
  
 [Birbirine Kenetlenmiş İşlemler](../../../docs/standard/threading/interlocked-operations.md)  
 Nasıl kullanılacağını açıklar <xref:System.Threading.Interlocked> artırın veya bir değer azaltma ve tek bir atomik işlemde değeri depolamak için sınıf.  
  
 [Okuyucu-Yazıcı Kilitleri](../../../docs/standard/threading/reader-writer-locks.md)  
 Tek yazıcı/birden çok okuyucu semantiği uygulayan bir kilit tanımlar.  
  
 [Semaphore ve SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)  
 Açıklar <xref:System.Threading.Semaphore> nesneleri ve bunları sınırlı kaynaklara erişimi denetlemek için nasıl kullanılacağını açıklar.  
  
 [Eşitleme Temellerine Genel Bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 .NET Framework sınıfları kilitleme ve yönetilen iş parçacıklarını eşitleme için sağlanan özellikler karşılaştırılmaktadır.  
  
 [Engel](../../../docs/standard/threading/barrier.md)  
 Açıklar <xref:System.Threading.Barrier> koordinasyon iş parçacıklarının engeli desenini aşamalı işlemlerinde uygulayan nesneler.  
  
 [SpinLock](../../../docs/standard/threading/spinlock.md)  
 Açıklar <xref:System.Threading.SpinLock>, hafif bir izleme sınıfı belirli bir alt düzey senaryoları için alternatif.  
  
 [SpinWait](../../../docs/standard/threading/spinwait.md)  
 Açıklar <xref:System.Threading.SpinWait>, düşük düzeyli eşitleme temel nesne çekirdek tabanlı bekleme başlatmadan önce meşgul dönme gerçekleştirir.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Threading.Thread>  
 İçin başvuru belgeleri sağlar **iş parçacığı** yönetilmeyen koddan gelen veya yönetilen bir uygulamada oluşturulan yönetilen iş parçacığı temsil eden sınıf.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Arka plan görevleri, kullanıcı arabirimi iş parçacığında harekete geçirilen olayları aracılığıyla iletişim kuran kullanıcı arabirimi ile etkileşim sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Zaman Uyumsuz Dosya G/Ç](../../../docs/standard/io/asynchronous-file-i-o.md)  
 Nasıl g/ç zaman uyumsuz tamamlama bağlantı noktalarını yalnızca bir giriş/çıkış işlemi tamamlandığında işleme gerektirecek şekilde iş parçacığı havuzu kullanma açıklar.  
  
 [Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 Çok iş parçacıklı programlama için önerilen yaklaşım açıklar [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] ve daha sonra.
