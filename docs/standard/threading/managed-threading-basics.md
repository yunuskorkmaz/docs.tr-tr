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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5fa91bb22de6492815f79bfd50e1fefc800c6047
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586519"
---
# <a name="managed-threading-basics"></a>Yönetilen İş Parçacığı Oluşturma Temelleri
Bu bölümde, ilk beş konular yönetilen iş parçacığı oluşturma kullanın ve bazı temel özellikleri açıklamak için ne zaman belirlemenize yardımcı olmak için tasarlanmıştır. Ek özellikler sağlayan sınıflar hakkında daha fazla bilgi için bkz: [iş parçacığı nesneleri ve özellikleri](../../../docs/standard/threading/threading-objects-and-features.md) ve [eşitleme temellerine genel bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Bu bölümde kapak konularında kalan konular Windows işletim sistemiyle yönetilen iş parçacığı oluşturma etkileşimi dahil olmak üzere, Gelişmiş.  
  
> [!NOTE]
>  İçinde [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], görev paralel kitaplığı ve PLINQ'da çok iş parçacıklı programlar görev ve veri paralellik için API'ler sağlar. Daha fazla bilgi için bkz: [paralel programlama](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [İş Parçacıkları ve İş Parçacığı Oluşturma](../../../docs/standard/threading/threads-and-threading.md)  
 Avantajları ve dezavantajları birden çok iş parçacığı açıklar ve hangi iş parçacığı oluşturabilir veya iş parçacığı havuzu iş parçacıkları kullanın senaryoları özetler.  
  
 [Yönetilen İş Parçacıklarında Özel Durumlar](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 .NET Framework'ün farklı sürümleri için iş parçacıklarında işlenmeyen özel durumlar davranışını durumlarda özellikle açıklar, bunlar sonlandırılmasıyla uygulamanın neden olarak.  
  
 [Çoklu İş Parçacığı Kullanımı için Veri Eşitleme](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 Birden çok iş parçacığı ile kullanılacak sınıfları verileri eşitlemek için stratejilerini açıklar.  
  
 [Yönetilen İş Parçacığı Durumları](../../../docs/standard/threading/managed-thread-states.md)  
 Temel iş parçacığı durumları ve bir iş parçacığı çalışır durumda olup olmadığını algılamak nasıl açıklanmaktadır.  
  
 [Ön Plan ve Arka Plan İş Parçacıkları](../../../docs/standard/threading/foreground-and-background-threads.md)  
 Ön ve arka plan iş parçacıkları arasındaki farklar açıklanmaktadır.  
  
 [Windows'ta Yönetilen ve Yönetilmeyen İş Parçacığı Oluşturma](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 COM grupların ve yönetilen iş parçacığı etkileşimini açıklar ve yönetilen eşdeğerlerini API'leri iş parçacığı oluşturma Windows için listeler veya yönetilen ve yönetilmeyen iş parçacığı oluşturma arasındaki ilişkiyi açıklar.  
  
 [Thread.Suspend, Atık Toplama ve Güvenli Noktalar](../../../docs/standard/threading/thread-suspend-garbage-collection-and-safe-points.md)  
 İş parçacığı askıya alma ve atık toplama açıklar.  
  
 [İş Parçacığı Yerel Deposu: İş Parçacığı Göreli Statik Alanları ve Veri Yuvaları](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 İş parçacığı göreli depolama mekanizmaları açıklar.  
  
 [Yönetilen İş Parçacıklarında İptal](../../../docs/standard/threading/cancellation-in-managed-threads.md)  
 Ne zaman uyumsuz veya uzun süre çalışan zaman uyumlu işlemler açıklayan bir iptal belirteci kullanarak iptal edilebilir.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Threading.Thread>  
 Başvuru belgelerine sağlar **iş parçacığı** yönetilmeyen koddan gelen veya yönetilen bir uygulamada oluşturuldu, yönetilen bir iş parçacığı temsil eden sınıf.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Uygulamak için güvenli bir yol sağlar kullanıcı arabirimi nesneleri ile birlikte çoklu iş parçacığı kullanımı.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Eşitleme Temellerine Genel Bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 Birden çok iş parçacığı etkinliklerini eşitlemek için kullanılan yönetilen sınıflar açıklanmaktadır.  
  
 [Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri](../../../docs/standard/threading/managed-threading-best-practices.md)  
 Yaygın sorunları açıklar çoklu iş parçacığı kullanımı ve sorunlarını stratejileri.  
  
 [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)  
 Zaman uyumsuz ve çok iş parçacıklı .NET Framework uygulamaları oluşturma işini büyük ölçüde kolaylaştırma görev paralel kitaplığı ve PLINQ'da, açıklar.
