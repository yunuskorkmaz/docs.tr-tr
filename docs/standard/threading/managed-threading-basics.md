---
title: Yönetilen İş Parçacığı Oluşturma Temelleri
description: Özel durumlar, verileri eşitleme, ön plan & arka plan iş parçacıkları, yerel depolama ve daha fazlası gibi konuları kapsayan diğer yönetilen iş parçacığı makalelerine yönelik bağlantılara bakın.
ms.date: 03/30/2017
helpviewer_keywords:
- multiple threads
- threading [.NET], multiple threads
- threading [.NET], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
ms.openlocfilehash: 16785b1c21c5810e55429f6756dcf591c90d8499
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94819675"
---
# <a name="managed-threading-basics"></a>Yönetilen iş parçacığı temelleri

Bu bölümün ilk beş makalesi, yönetilen iş parçacığı oluşturmayı ve bazı temel özellikleri açıklamak için ne zaman kullanacağınızı belirlemenize yardımcı olmak üzere tasarlanmıştır. Ek özellikler sağlayan sınıflar hakkında daha fazla bilgi için bkz. [Iş parçacığı nesneleri ve özellikleri](threading-objects-and-features.md) ve [eşitleme temel bilgilerine genel bakış](overview-of-synchronization-primitives.md).  
  
 Bu bölümdeki diğer makaleler, Windows işletim sistemi ile yönetilen iş parçacığı etkileşimi de dahil olmak üzere gelişmiş konuları kapsar.  
  
> [!NOTE]
> .NET Framework 4 ' den başlayarak, görev paralel kitaplığı ve PLıNQ, çok iş parçacıklı programlarda görev ve veri paralelliği için API 'Ler sağlar. Daha fazla bilgi için bkz. [paralel programlama](../parallel-programming/index.md).  
  
## <a name="in-this-section"></a>Bu bölümde

 [İş Parçacıkları ve İş Parçacığı Oluşturma](threads-and-threading.md)  
 Birden çok iş parçacığının avantajlarını ve dezavantajını açıklar ve iş parçacıkları oluşturabileceğiniz veya iş parçacığı havuzu iş parçacıklarını kullanabileceğiniz senaryoları özetler.  
  
 [Yönetilen İş Parçacıklarında Özel Durumlar](exceptions-in-managed-threads.md)  
 .NET 'in farklı sürümleri için iş parçacıklarında işlenmeyen özel durumların davranışını, özellikle de uygulamanın sonlandırılması ile sonuçlandığı durumlarda açıklar.  
  
 [Çoklu İş Parçacığı Kullanımı için Veri Eşitleme](synchronizing-data-for-multithreading.md)  
 Birden çok iş parçacığı ile kullanılacak sınıflardaki verileri eşitlemeye yönelik stratejileri açıklar.  
  
 [Ön Plan ve Arka Plan İş Parçacıklarını Seçme](foreground-and-background-threads.md)  
 Ön plan ve arka plan iş parçacıkları arasındaki farklılıkları açıklar.  
  
 [Windows'da Yönetilen ve Yönetilmeyen İş Parçacığı Oluşturma](managed-and-unmanaged-threading-in-windows.md)  
 Yönetilen ve yönetilmeyen iş parçacığı arasındaki ilişkiyi açıklar, Windows iş parçacığı oluşturma API 'Lerinin yönetilen eşdeğerlerini listeler ve COM apartmanlarının ve yönetilen iş parçacıklarının etkileşimini tartışır.  
  
 [İş Parçacığında Yerel Depolama: İş Parçacığı Göreli Statik Alanları ve Veri Yuvaları](thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 İş parçacığı göreli depolama mekanizmalarını açıklar.  
  
## <a name="reference"></a>Başvuru

 <xref:System.Threading.Thread>  
 Yönetilen bir iş parçacığını temsil eden, yönetilmeyen koddan geldiği veya yönetilen bir uygulamada oluşturulup oluşturulmayacağı **Iş parçacığı** sınıfı için başvuru belgeleri sağlar.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Kullanıcı arabirimi nesneleriyle birlikte çoklu iş parçacığı uygulama için güvenli bir yol sağlar.  
  
## <a name="related-sections"></a>İlgili bölümler

 [Eşitleme temelleri 'ne genel bakış](overview-of-synchronization-primitives.md)  
 Birden çok iş parçacığının etkinliklerini eşleştirmek için kullanılan yönetilen sınıfları açıklar.  
  
 [Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri](managed-threading-best-practices.md)  
 Çoklu iş parçacığı ve stratejilerle ilgili yaygın sorunları açıklar.  
  
 [Paralel programlama](../parallel-programming/index.md)  
 Zaman uyumsuz ve çok iş parçacıklı .NET uygulamaları oluşturma işini büyük ölçüde kolaylaştıran paralel kitaplığı ve PLıNQ görevini açıklar.
