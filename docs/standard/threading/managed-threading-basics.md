---
title: Yönetilen İş Parçacığı Oluşturma Temelleri
description: Özel durumlar, verileri eşitleme, ön plan & arka plan iş parçacıkları, yerel depolama ve daha fazlası gibi konuları kapsayan diğer yönetilen iş parçacığı makalelerine yönelik bağlantılara bakın.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET Framework], multiple threads
- threading [.NET Framework], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
ms.openlocfilehash: d4a4ceabf29bd0f6f537e59ba477f9da686b1ef5
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769099"
---
# <a name="managed-threading-basics"></a>Yönetilen iş parçacığı temelleri

Bu bölümün ilk beş konusu, yönetilen iş parçacığı kullanmanın ne zaman kullanılacağını ve bazı temel özellikleri açıklamanıza yardımcı olmak üzere tasarlanmıştır. Ek özellikler sağlayan sınıflar hakkında daha fazla bilgi için bkz. [Iş parçacığı nesneleri ve özellikleri](threading-objects-and-features.md) ve [eşitleme temel bilgilerine genel bakış](overview-of-synchronization-primitives.md).  
  
 Bu bölümdeki konuların geri kalanı, Windows işletim sistemi ile yönetilen iş parçacığı etkileşimi de dahil olmak üzere gelişmiş konuları kapsar.  
  
> [!NOTE]
> .NET Framework 4 ' te, görev paralel kitaplığı ve PLıNQ, çok iş parçacıklı programlarda görev ve veri paralelliği için API 'Ler sağlar. Daha fazla bilgi için bkz. [paralel programlama](../parallel-programming/index.md).  
  
## <a name="in-this-section"></a>Bu bölümde

 [İş Parçacıkları ve İş Parçacığı Oluşturma](threads-and-threading.md)  
 Birden çok iş parçacığının avantajlarını ve dezavantajını açıklar ve iş parçacıkları oluşturabileceğiniz veya iş parçacığı havuzu iş parçacıklarını kullanabileceğiniz senaryoları özetler.  
  
 [Yönetilen İş Parçacıklarında Özel Durumlar](exceptions-in-managed-threads.md)  
 Farklı .NET Framework sürümleri için iş parçacıklarında işlenmeyen özel durumların davranışını, özellikle de uygulamanın sonlandırmasına neden oldukları durumları açıklar.  
  
 [Çoklu İş Parçacığı Kullanımı için Veri Eşitleme](synchronizing-data-for-multithreading.md)  
 Birden çok iş parçacığı ile kullanılacak sınıflardaki verileri eşitlemeye yönelik stratejileri açıklar.  
  
 [Ön Plan ve Arka Plan İş Parçacıkları](foreground-and-background-threads.md)  
 Ön plan ve arka plan iş parçacıkları arasındaki farklılıkları açıklar.  
  
 [Windows'ta Yönetilen ve Yönetilmeyen İş Parçacığı Oluşturma](managed-and-unmanaged-threading-in-windows.md)  
 Yönetilen ve yönetilmeyen iş parçacığı arasındaki ilişkiyi açıklar, Windows iş parçacığı oluşturma API 'Lerinin yönetilen eşdeğerlerini listeler ve COM apartmanlarının ve yönetilen iş parçacıklarının etkileşimini tartışır.  
  
 [İş Parçacığı Yerel Deposu: İş Parçacığı Göreli Statik Alanları ve Veri Yuvaları](thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
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
 Zaman uyumsuz ve çok iş parçacıklı .NET Framework uygulamaları oluşturma işini büyük ölçüde kolaylaştıran paralel kitaplığı ve PLıNQ görevini açıklar.
