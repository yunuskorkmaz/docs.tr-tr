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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139235"
---
# <a name="managed-threading-basics"></a>Yönetilen iş parçacığı temelleri

Bu bölümün ilk beş konusu, yönetilen iş parçacığı kullanmanın ne zaman kullanılacağını ve bazı temel özellikleri açıklamanıza yardımcı olmak üzere tasarlanmıştır. Ek özellikler sağlayan sınıflar hakkında daha fazla bilgi için bkz. [Iş parçacığı nesneleri ve özellikleri](../../../docs/standard/threading/threading-objects-and-features.md) ve [eşitleme temel bilgilerine genel bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Bu bölümdeki konuların geri kalanı, Windows işletim sistemi ile yönetilen iş parçacığı etkileşimi de dahil olmak üzere gelişmiş konuları kapsar.  
  
> [!NOTE]
> .NET Framework 4 ' te, görev paralel kitaplığı ve PLıNQ, çok iş parçacıklı programlarda görev ve veri paralelliği için API 'Ler sağlar. Daha fazla bilgi için bkz. [paralel programlama](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="in-this-section"></a>Bu bölümde

 [İş Parçacıkları ve İş Parçacığı Oluşturma](../../../docs/standard/threading/threads-and-threading.md)  
 Birden çok iş parçacığının avantajlarını ve dezavantajını açıklar ve iş parçacıkları oluşturabileceğiniz veya iş parçacığı havuzu iş parçacıklarını kullanabileceğiniz senaryoları özetler.  
  
 [Yönetilen İş Parçacıklarında Özel Durumlar](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 Farklı .NET Framework sürümleri için iş parçacıklarında işlenmeyen özel durumların davranışını, özellikle de uygulamanın sonlandırmasına neden oldukları durumları açıklar.  
  
 [Çoklu İş Parçacığı Kullanımı için Veri Eşitleme](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 Birden çok iş parçacığı ile kullanılacak sınıflardaki verileri eşitlemeye yönelik stratejileri açıklar.  
  
 [Ön Plan ve Arka Plan İş Parçacıkları](../../../docs/standard/threading/foreground-and-background-threads.md)  
 Ön plan ve arka plan iş parçacıkları arasındaki farklılıkları açıklar.  
  
 [Windows'ta Yönetilen ve Yönetilmeyen İş Parçacığı Oluşturma](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 Yönetilen ve yönetilmeyen iş parçacığı arasındaki ilişkiyi açıklar, Windows iş parçacığı oluşturma API 'Lerinin yönetilen eşdeğerlerini listeler ve COM apartmanlarının ve yönetilen iş parçacıklarının etkileşimini tartışır.  
  
 [İş Parçacığı Yerel Deposu: İş Parçacığı Göreli Statik Alanları ve Veri Yuvaları](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 İş parçacığı göreli depolama mekanizmalarını açıklar.  
  
## <a name="reference"></a>Başvuru

 <xref:System.Threading.Thread>  
 Yönetilen bir iş parçacığını temsil eden, yönetilmeyen koddan geldiği veya yönetilen bir uygulamada oluşturulup oluşturulmayacağı **Iş parçacığı** sınıfı için başvuru belgeleri sağlar.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Kullanıcı arabirimi nesneleriyle birlikte çoklu iş parçacığı uygulama için güvenli bir yol sağlar.  
  
## <a name="related-sections"></a>İlgili bölümler

 [Eşitleme Temellerine Genel Bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 Birden çok iş parçacığının etkinliklerini eşleştirmek için kullanılan yönetilen sınıfları açıklar.  
  
 [Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri](../../../docs/standard/threading/managed-threading-best-practices.md)  
 Çoklu iş parçacığı ve stratejilerle ilgili yaygın sorunları açıklar.  
  
 [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)  
 Zaman uyumsuz ve çok iş parçacıklı .NET Framework uygulamaları oluşturma işini büyük ölçüde kolaylaştıran paralel kitaplığı ve PLıNQ görevini açıklar.
