---
title: Yönetilen İş Parçacığı Oluşturma Temelleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET Framework], multiple threads
- threading [.NET Framework], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
ms.openlocfilehash: bec769043ab630b37609bed12302ceff5b90474a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139235"
---
# <a name="managed-threading-basics"></a>Yönetilen iş parçacığı temelleri

Bu bölümün ilk beş konusu, yönetilen iş parçacığının ne zaman kullanılacağını belirlemenize ve bazı temel özellikleri açıklamanıza yardımcı olmak için tasarlanmıştır. Ek özellikler sağlayan sınıflar hakkında bilgi için [bkz.](../../../docs/standard/threading/threading-objects-and-features.md) [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
  
 Bu bölümdeki diğer konular, yönetilen iş parçacığının Windows işletim sistemiyle etkileşimi de dahil olmak üzere gelişmiş konuları kapsamaktadır.  
  
> [!NOTE]
> .NET Framework 4'te, Görev Paralel Kitaplığı ve PLINQ çok iş parçacığı lı programlarda görev ve veri paralelliği için API'ler sağlar. Daha fazla bilgi için [Bkz. Paralel Programlama.](../../../docs/standard/parallel-programming/index.md)  
  
## <a name="in-this-section"></a>Bu bölümde

 [İş Parçacıkları ve İş Parçacığı Oluşturma](../../../docs/standard/threading/threads-and-threading.md)  
 Birden çok iş parçacığının avantajlarını ve dezavantajlarını tartışır ve iş parçacığı oluşturabileceğiniz veya iş parçacığı havuzu iş parçacığı iş parçacığı kullanabileceğiniz senaryoları özetler.  
  
 [Yönetilen İş Parçacıklarında Özel Durumlar](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 .NET Framework'ün farklı sürümleri için işlenmemiş özel durumların davranışını, özellikle de uygulamanın sonlandırılmasıyla sonuçlanan durumları açıklar.  
  
 [Çoklu İş Parçacığı Kullanımı için Veri Eşitleme](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 Birden çok iş parçacığı ile kullanılacak sınıflarda verileri eşitleme stratejilerini açıklar.  
  
 [Ön Plan ve Arka Plan İş Parçacıkları](../../../docs/standard/threading/foreground-and-background-threads.md)  
 Ön plan ve arka plan iş parçacıkları arasındaki farkları açıklar.  
  
 [Windows'ta Yönetilen ve Yönetilmeyen İş Parçacığı Oluşturma](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 Yönetilen ve yönetilmeyen iş parçacığı arasındaki ilişkiyi tartışır, Windows iş parçacığı API'leri için yönetilen eşdeğerleri listeler ve COM daireleri ve yönetilen iş parçacıklarının etkileşimini tartışır.  
  
 [İş Parçacığı Yerel Deposu: İş Parçacığı Göreli Statik Alanları ve Veri Yuvaları](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 İş parçacığı göreli depolama mekanizmalarını açıklar.  
  
## <a name="reference"></a>Başvuru

 <xref:System.Threading.Thread>  
 Yönetilmeyen koddan gelen veya yönetilen bir uygulamada oluşturulan olsun, yönetilen bir iş parçacığı temsil eden **İş Parçacığı** sınıfı için başvuru belgeleri sağlar.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Kullanıcı arabirimi nesneleri ile birlikte çoklu iş parçacığı uygulamak için güvenli bir yol sağlar.  
  
## <a name="related-sections"></a>İlgili bölümler

 [Senkronizasyon İlkellerine Genel Bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 Birden çok iş parçacığının etkinliklerini eşitlemek için kullanılan yönetilen sınıfları açıklar.  
  
 [Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri](../../../docs/standard/threading/managed-threading-best-practices.md)  
 Çok iş parçacığı ile ilgili yaygın sorunları ve sorunları önlemek için stratejiler açıklar.  
  
 [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)  
 Asynchronous ve çok iş parçacığı .NET Framework uygulamaları oluşturma işini büyük ölçüde basitleştiren Görev Paralel Kitaplığı ve PLINQ'u açıklar.
