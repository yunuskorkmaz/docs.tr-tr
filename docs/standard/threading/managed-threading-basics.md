---
title: "Yönetilen İş Parçacığı Oluşturma Temelleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multiple threads
- threading [.NET Framework], multiple threads
- threading [.NET Framework], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 62c207f6074e33813887c6903f5285ee72d14e85
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="managed-threading-basics"></a>Yönetilen İş Parçacığı Oluşturma Temelleri
Bu bölümde, ilk beş konular yönetilen iş parçacığı oluşturma kullanın ve bazı temel özellikleri açıklamak için ne zaman belirlemenize yardımcı olmak için tasarlanmıştır. Ek özellikler sağlayan sınıflar hakkında daha fazla bilgi için bkz: [iş parçacığı nesneleri ve özellikleri](../../../docs/standard/threading/threading-objects-and-features.md) ve [eşitleme temellerine genel bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Bu bölümde kapak konularında kalan konular Windows işletim sistemiyle yönetilen iş parçacığı oluşturma etkileşimi dahil olmak üzere, Gelişmiş.  
  
> [!NOTE]
>  İçinde [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], görev paralel kitaplığı ve PLINQ'da çok iş parçacıklı programlar görev ve veri paralellik için API'ler sağlar. Daha fazla bilgi için bkz: [paralel programlama](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [İş parçacıkları ve iş parçacığı oluşturma](../../../docs/standard/threading/threads-and-threading.md)  
 Avantajları ve dezavantajları birden çok iş parçacığı açıklar ve hangi iş parçacığı oluşturabilir veya iş parçacığı havuzu iş parçacıkları kullanın senaryoları özetler.  
  
 [Yönetilen iş parçacıklarında özel durumlar](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 .NET Framework'ün farklı sürümleri için iş parçacıklarında işlenmeyen özel durumlar davranışını durumlarda özellikle açıklar, bunlar sonlandırılmasıyla uygulamanın neden olarak.  
  
 [İçin Veri Eşitleme çoklu iş parçacığı kullanımı](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 Birden çok iş parçacığı ile kullanılacak sınıfları verileri eşitlemek için stratejilerini açıklar.  
  
 [Yönetilen iş parçacığı durumları](../../../docs/standard/threading/managed-thread-states.md)  
 Temel iş parçacığı durumları ve bir iş parçacığı çalışır durumda olup olmadığını algılamak nasıl açıklanmaktadır.  
  
 [Ön plan ve arka plan iş parçacıkları](../../../docs/standard/threading/foreground-and-background-threads.md)  
 Ön ve arka plan iş parçacıkları arasındaki farklar açıklanmaktadır.  
  
 [Windows'da yönetilen ve yönetilmeyen iş parçacığı oluşturma](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 COM grupların ve yönetilen iş parçacığı etkileşimini açıklar ve yönetilen eşdeğerlerini API'leri iş parçacığı oluşturma Windows için listeler veya yönetilen ve yönetilmeyen iş parçacığı oluşturma arasındaki ilişkiyi açıklar.  
  
 [Thread.Suspend çöp toplama ve güvenli noktalar](../../../docs/standard/threading/thread-suspend-garbage-collection-and-safe-points.md)  
 İş parçacığı askıya alma ve atık toplama açıklar.  
  
 [İş parçacığı yerel depolama: İş parçacığı göreli statik alanları ve veri yuvaları](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 İş parçacığı göreli depolama mekanizmaları açıklar.  
  
 [Yönetilen iş parçacıklarında iptal](../../../docs/standard/threading/cancellation-in-managed-threads.md)  
 Ne zaman uyumsuz veya uzun süre çalışan zaman uyumlu işlemler açıklayan bir iptal belirteci kullanarak iptal edilebilir.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Threading.Thread>  
 Başvuru belgelerine sağlar **iş parçacığı** yönetilmeyen koddan gelen veya yönetilen bir uygulamada oluşturuldu, yönetilen bir iş parçacığı temsil eden sınıf.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Uygulamak için güvenli bir yol sağlar kullanıcı arabirimi nesneleri ile birlikte çoklu iş parçacığı kullanımı.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Eşitleme temellerine genel bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 Birden çok iş parçacığı etkinliklerini eşitlemek için kullanılan yönetilen sınıflar açıklanmaktadır.  
  
 [Yönetilen iş parçacığı oluşturma en iyi uygulamalar](../../../docs/standard/threading/managed-threading-best-practices.md)  
 Yaygın sorunları açıklar çoklu iş parçacığı kullanımı ve sorunlarını stratejileri.  
  
 [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)  
 Zaman uyumsuz ve çok iş parçacıklı .NET Framework uygulamaları oluşturma işini büyük ölçüde kolaylaştırma görev paralel kitaplığı ve PLINQ'da, açıklar.
