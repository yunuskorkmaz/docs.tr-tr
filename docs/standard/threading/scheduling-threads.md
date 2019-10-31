---
title: İş parçacıklarını zamanlama
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], scheduling
- scheduling threads
ms.assetid: 67e4a0eb-3095-4ea7-b20f-908faa476277
ms.openlocfilehash: abcdf56b90513b937adefc38583e0312fec69785
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73106225"
---
# <a name="scheduling-threads"></a>İş parçacıklarını zamanlama

Her iş parçacığının kendisine atanmış bir iş parçacığı önceliği vardır. Ortak dil çalışma zamanı içinde oluşturulan iş parçacıklarına başlangıçta <xref:System.Threading.ThreadPriority.Normal?displayProperty=nameWithType>önceliği atanır. Çalışma zamanının dışında oluşturulan iş parçacıkları, yönetilen ortama girmeden önce sahip oldukları önceliği korurlar. <xref:System.Threading.Thread.Priority?displayProperty=nameWithType> özelliği ile herhangi bir iş parçacığının önceliğini alabilir veya ayarlayabilirsiniz.  
  
 İş parçacıkları önceliklerine göre yürütme için zamanlanır. İş parçacıkları çalışma zamanı içinde yürütülebilse de, tüm iş parçacıkları işletim sistemi tarafından işlemci zamanı dilimlerine atanır. İş parçacıklarının yürütüldüğü sırayı belirlemede kullanılan zamanlama algoritmasının ayrıntıları her bir işletim sistemiyle farklılık gösterir. Bazı işletim sistemleri altında, en yüksek önceliğe sahip iş parçacığı (yürütülebilecek iş parçacıklarından) her zaman ilk çalışacak şekilde zamanlanır. Aynı önceliğe sahip birden çok iş parçacığı varsa, Zamanlayıcı ilgili öncelikteki iş parçacıkları arasında geçiş yapar ve her iş parçacığına yürütülecek sabit bir zaman dilimi verir. Daha yüksek önceliğe sahip bir iş parçacığı çalıştırmak için kullanılabilir olduğu sürece, düşük öncelikli iş parçacıkları yürütülmeye ulaşmaz. Belirli bir önceliğe göre daha fazla çalıştırılabilir iş parçacığı kalmadığında, Zamanlayıcı bir sonraki düşük önceliğe gider ve yürütme için bu öncelikteki iş parçacıklarını zamanlar. Daha yüksek öncelikli bir iş parçacığı çalıştırılabilir hale gelirse, daha düşük öncelikli iş parçacığı yok edilir ve daha yüksek öncelikli iş parçacığının bir kez daha yürütülmesine izin verilir. Her birinin üzerine, işletim sistemi, bir uygulamanın kullanıcı arabirimi ön plan ve arka plan arasında taşındığında, iş parçacığı önceliklerini dinamik olarak da ayarlayabilir. Diğer işletim sistemleri farklı bir zamanlama algoritması kullanmayı tercih edebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Parçacıkları ve İş Parçacığı Oluşturmayı Kullanma](../../../docs/standard/threading/using-threads-and-threading.md)
- [Windows'ta Yönetilen ve Yönetilmeyen İş Parçacığı Oluşturma](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)
