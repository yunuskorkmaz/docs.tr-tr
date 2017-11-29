---
title: "İş Parçacığı Nesneleri ve Özellikleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2a73e5c60a661c171e9e46e6307484cf5e0e6b80
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="threading-objects-and-features"></a>İş Parçacığı Nesneleri ve Özellikleri
.NET Framework yardımcı nesne sayısı sağlar birden çok iş parçacıklı uygulamaları oluşturmak ve yönetmek. Yönetilen iş parçacığı tarafından gösterilen <xref:System.Threading.Thread> sınıfı. <xref:System.Threading.ThreadPool> Sınıfı, kolay oluşturulmasını ve birden çok iş parçacıklı arka plan görevleri yönetimini sağlar. <xref:System.ComponentModel.BackgroundWorker> Sınıfı kullanıcı arabirimiyle etkileşim görevler için aynı değil. <xref:System.Threading.Timer> Sınıfı zaman aralıklarında arka plan görevleri yürütür.  
  
 Ayrıca, bir dizi etkinlikler dahil olmak üzere iş parçacığı eşitleme sınıfları vardır <xref:System.Threading.Semaphore> ve <xref:System.Threading.EventWaitHandle> .NET Framework 2.0 sürümünde sunulan sınıfları. Bu sınıfların özelliklerini de karşılaştırılır [eşitleme temellerine genel bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Yönetilen iş parçacığı havuzu](../../../docs/standard/threading/the-managed-thread-pool.md)  
 Açıklar **Threadpool'u** herhangi bir iş parçacığı yönetim kendiniz yapmak zorunda kalmadan bir görevi çalıştırmak için bir iş parçacığı isteği sağlayan sınıf.  
  
 [Zamanlayıcılar](../../../docs/standard/threading/timers.md)  
 Nasıl kullanılacağı açıklanmaktadır bir **Zamanlayıcı** belirli bir zamanda çağrılan bir temsilciyi belirtmek için.  
  
 [İzleyicileri](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 Nasıl kullanılacağı açıklanmaktadır **İzleyici** sınıf üyesi erişimi eşitlemek için ya da kendi iş parçacığı yönetim türleri oluşturmak için.  
  
 [Bekleme tanıtıcıları](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 Açıklar <xref:System.Threading.WaitHandle> sınıfı, olay için Özet temel sınıf bekleme tanıtıcıları, zaman uyumu sağlayıcılar ve birden çok eşitleme olay bekleniyor etkinleştirir semafor.  
  
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 Sinyal ve sinyalleri için bekleyen iş parçacığı etkinliklerini eşitlemek için kullanılan yönetilen olay bekleme tanıtıcıları açıklar.  
  
 [Zaman uyumu sağlayıcılar](../../../docs/standard/threading/mutexes.md)  
 Nasıl kullanılacağı açıklanmaktadır bir <xref:System.Threading.Mutex> bir nesneye erişimi eşitlemek ya da kendi eşitleme mekanizmaları oluşturmak için.  
  
 [Birbirine kenetlenmiş işlemler](../../../docs/standard/threading/interlocked-operations.md)  
 Nasıl kullanılacağı açıklanmaktadır <xref:System.Threading.Interlocked> artırın veya bir değer azaltma ve tek bir atomik işlemle değeri depolamak için sınıf.  
  
 [Okuyucu-Yazıcı kilitleri](../../../docs/standard/threading/reader-writer-locks.md)  
 Tek yazıcı/birden çok okuyucu semantiğini uygular bir kilit tanımlar.  
  
 [Semafor ve SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)  
 Açıklar <xref:System.Threading.Semaphore> nesnelerini ve bunların sınırlı kaynaklara erişimi denetlemek için nasıl kullanılacağını açıklar.  
  
 [Eşitleme temellerine genel bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 Kilitleme ve yönetilen iş parçacıklarını eşitleme için sağlanan .NET Framework sınıfları özellikleri karşılaştırılır.  
  
 [Engelle](../../../docs/standard/threading/barrier.md)  
 Açıklar <xref:System.Threading.Barrier> aşamalı işlemlerinde düzenleme iş parçacığı engel desenini uygulayan nesneler.  
  
 [SpinLock](../../../docs/standard/threading/spinlock.md)  
 Açıklar <xref:System.Threading.SpinLock>, alt düzey belirli senaryolar için izleme sınıfı için basit bir alternatif.  
  
 [SpinWait](../../../docs/standard/threading/spinwait.md)  
 Açıklar <xref:System.Threading.SpinWait>, düşük düzeyli eşitleme ilkel çekirdek tabanlı bekleme başlatmadan önce meşgul dönen gerçekleştirir.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Threading.Thread>  
 Başvuru belgelerine sağlar **iş parçacığı** yönetilmeyen koddan gelen veya yönetilen bir uygulamada oluşturuldu, yönetilen bir iş parçacığı temsil eden sınıf.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Kullanıcı arabirimi iş parçacığı üzerinde oluşturulan olaylara aracılığıyla iletişim kurmasını kullanıcı arabirimiyle etkileşim arka plan görevleri sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Zaman uyumsuz dosya g/ç](../../../docs/standard/io/asynchronous-file-i-o.md)  
 İş parçacığı havuzu g/ç zaman uyumsuz tamamlama bağlantı noktalarını yalnızca bir giriş/çıkış işlem tamamlandığında işleme gerektiren için nasıl kullanıldığını açıklar.  
  
 [Görev paralel kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 Birden çok iş parçacıklı programlama için önerilen yaklaşım açıklar [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] ve daha sonra.
