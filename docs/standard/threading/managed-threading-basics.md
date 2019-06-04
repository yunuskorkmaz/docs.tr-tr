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
ms.openlocfilehash: a47946ab8eb26045e641c44642bfe7a026269f3d
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486335"
---
# <a name="managed-threading-basics"></a>Yönetilen iş parçacığı oluşturma temelleri

Bu bölümün ilk beş konular, yönetilen iş parçacığı kullanılacağını ve bazı temel özellikleri açıklamak için ne zaman belirlemenize yardımcı olmak için tasarlanmıştır. Ek özellikler sağlayan sınıflar hakkında daha fazla bilgi için bkz: [iş parçacığı nesneleri ve özellikleri](../../../docs/standard/threading/threading-objects-and-features.md) ve [eşitleme temellerine genel bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Bu bölümde kapak konularındaki geri kalanı Windows işletim sistemi ile yönetilen iş parçacığı etkileşimi gibi konuları, Gelişmiş.  
  
> [!NOTE]
>  .NET Framework 4'te, görev paralel kitaplığı ve PLINQ'da, çok iş parçacıklı programlarda görev ve veri paralelliği için API'leri sağlar. Daha fazla bilgi için [paralel programlama](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="in-this-section"></a>Bu bölümde

 [İş Parçacıkları ve İş Parçacığı Oluşturma](../../../docs/standard/threading/threads-and-threading.md)  
 Avantajları ve dezavantajları birden çok iş parçacığı ele alır ve hangi iş parçacıkları oluşturma veya iş parçacığı havuzu iş parçacıkları kullanma senaryoları özetlenmiştir.  
  
 [Yönetilen İş Parçacıklarında Özel Durumlar](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 İşlenmeyen özel durumlar .NET Framework'ün farklı sürümleri için iş parçacıklarında davranışını özellikle durumlar açıklanır, bunlar uygulama sonlandırmada neden olarak.  
  
 [Çoklu İş Parçacığı Kullanımı için Veri Eşitleme](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 Birden çok iş parçacığı ile kullanılacak sınıflardaki verileri eşitlemek için stratejilerini açıklar.  
  
 [Ön Plan ve Arka Plan İş Parçacıkları](../../../docs/standard/threading/foreground-and-background-threads.md)  
 Ön ve arka plan iş parçacıkları arasındaki farklar açıklanmaktadır.  
  
 [Windows'ta Yönetilen ve Yönetilmeyen İş Parçacığı Oluşturma](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 Yönetilen ve yönetilmeyen iş parçacığı oluşturma arasındaki ilişkiyi açıklar, Windows API iş parçacığı için yönetilen eşdeğerlerini listeler ve COM apartmanlar ve yönetilen iş parçacıklarını etkileşimi açıklanır.  
  
 [İş parçacığı yerel deposu: İş parçacığı göreli statik alanları ve veri yuvaları](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 İş parçacığı göreli depolama mekanizmalarını açıklar.  
  
## <a name="reference"></a>Başvuru

 <xref:System.Threading.Thread>  
 İçin başvuru belgeleri sağlar **iş parçacığı** yönetilmeyen koddan gelen veya yönetilen bir uygulamada oluşturulan yönetilen iş parçacığı temsil eden sınıf.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Uygulamak için güvenli bir yol sağlayan kullanıcı arabirimi nesneleri ile birlikte çoklu iş parçacığı kullanımı.  
  
## <a name="related-sections"></a>İlgili bölümler

 [Eşitleme Temellerine Genel Bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 Birden çok iş parçacığı etkinliklerini eşitlemek için kullanılan yönetilen sınıflar açıklanmaktadır.  
  
 [Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri](../../../docs/standard/threading/managed-threading-best-practices.md)  
 Ortak sorunları açıklar çoklu iş parçacığı kullanımı ve stratejileri sorunlarını önleme.  
  
 [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)  
 Görev paralel kitaplığı ve PLINQ'da, zaman uyumsuz ve çok iş parçacıklı .NET Framework uygulamaları oluşturma işini büyük ölçüde basitleştiren açıklar.
