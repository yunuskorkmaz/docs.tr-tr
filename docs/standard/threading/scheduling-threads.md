---
title: İş parçacıklarını zamanlama
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], scheduling
- scheduling threads
ms.assetid: 67e4a0eb-3095-4ea7-b20f-908faa476277
ms.openlocfilehash: abcdf56b90513b937adefc38583e0312fec69785
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73106225"
---
# <a name="scheduling-threads"></a>İş parçacıklarını zamanlama

Her iş parçacığı için atanmış bir iş parçacığı önceliği vardır. Ortak dil çalışma süresi içinde oluşturulan iş parçacıkları <xref:System.Threading.ThreadPriority.Normal?displayProperty=nameWithType>başlangıçta öncelik atanır. Çalışma zamanı dışında oluşturulan iş parçacıkları, yönetilen ortama girmeden önce sahip oldukları önceliği korur. <xref:System.Threading.Thread.Priority?displayProperty=nameWithType> Özellik ile herhangi bir iş parçacığının önceliğini alabilir veya ayarlayabilirsiniz.  
  
 İş parçacıkları, önceliklerine göre yürütülmesi için zamanlanır. İş parçacıkları çalışma süresi içinde yürütülse de, tüm iş parçacıklarına işletim sistemi tarafından işlemci zaman dilimleri atanır. İş parçacıklarının yürütülme sırasını belirlemek için kullanılan zamanlama algoritmasının ayrıntıları her işletim sistemine göre değişir. Bazı işletim sistemlerinde, en yüksek önceliğe (yürütülebilen iş parçacıklarının) iş parçacığı her zaman önce çalışacak şekilde zamanlanır. Aynı önceliğe sahip birden çok iş parçacığı varsa, zamanlayıcı bu öncelikteki iş parçacıkları arasında döner ve her iş parçacığına yürütülecek sabit bir zaman dilimi verir. Daha yüksek önceliğe sahip bir iş parçacığı çalıştırılabildiğiniz sürece, daha düşük öncelikli iş parçacıkları yürütülmez. Belirli bir öncelikte artık çalıştırılabilir iş parçacığı olmadığında, zamanlayıcı sonraki alt önceliğe taşınır ve iş parçacıklarını yürütme önceliğinde zamanlar. Daha yüksek öncelikli bir iş parçacığı çalıştırılabilir hale gelirse, daha düşük öncelik iş parçacığı önlenir ve daha yüksek öncelik iş parçacığı bir kez daha yürütülmesine izin verilir. Tüm bunların yanı sıra, bir uygulamanın kullanıcı arabirimi ön plan ve arka plan arasında taşındığıiçin işletim sistemi iş parçacığı önceliklerini dinamik olarak ayarlayabilir. Diğer işletim sistemleri farklı bir zamanlama algoritması kullanmayı seçebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Parçacığı ve İş Parçacığı kullanma](../../../docs/standard/threading/using-threads-and-threading.md)
- [Windows'ta Yönetilen ve Yönetilmeyen İş Parçacığı Oluşturma](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)
