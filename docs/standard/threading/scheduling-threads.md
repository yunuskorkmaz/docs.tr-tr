---
title: İş parçacıklarını zamanlama
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], scheduling
- scheduling threads
ms.assetid: 67e4a0eb-3095-4ea7-b20f-908faa476277
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 502e118a67e157ce7756efdece866564fddc6ab7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934309"
---
# <a name="scheduling-threads"></a>İş parçacıklarını zamanlama

Her iş parçacığı, kendisine atanmış bir iş parçacığı önceliği vardır. Ortak dil çalışma zamanı içinde oluşturulan iş parçacığı önceliği atanan başlangıçta <xref:System.Threading.ThreadPriority.Normal?displayProperty=nameWithType>. Çalışma zamanı dışında oluşturulan iş parçacığı yönetilen ortamı girildiğinde önce sahip oldukları öncelik korur. Get veya herhangi bir iş parçacığı ile önceliğini ayarlayın <xref:System.Threading.Thread.Priority?displayProperty=nameWithType> özelliği.  
  
 İş parçacıkları, önceliklerine göre yürütmek için zamanlanır. Tüm iş parçacıkları iş parçacıkları çalışma zamanı içinde yürütülen olsa da, işlemci zaman dilimleri işletim sistemi tarafından atanır. İş parçacıkları yürütüldüğü sırayı belirlemek için kullanılan algoritma zamanlama ayrıntılarını her işletim sistemiyle değişir. Bazı işletim sistemlerinde (yürütülebilir bu iş parçacığı)'ın en yüksek önceliğe sahip iş parçacığı her zaman ilk olarak çalıştırmak için zamanlandı. Aynı önceliğe sahip birden çok iş parçacığı her iş parçacığı bir sabit bir zaman dilimi yürütüleceği vererek, öncelik, iş parçacıklarının Zamanlayıcı dolaşma tüm kullanılabilir olması durumunda. Yüksek öncelikli bir iş parçacığı, çalıştırılmak için uygun olduğu sürece, daha düşük öncelikli iş parçacıklarını yürütmek almıyor. Belirli bir öncelikte artık çalıştırılabilir iş parçacıkları olduğunda Zamanlayıcı sonraki daha düşük önceliği taşır ve iş parçacıkları, öncelikle yürütme için zamanlanır. Daha yüksek öncelikli iş parçacığı çalıştırılabilir duruma gelirse, daha düşük öncelikli iş parçacığı etkisiz ve daha yüksek öncelikli iş parçacığını yeniden çalıştırmak için izin verilir. Bir uygulamanın kullanıcı arabirimini ön ve arka plan arasında geçirildiğinden tüm bunları en üstünde, işletim sistemini de iş parçacığı öncelikleri dinamik olarak ayarlayabilirsiniz. Diğer işletim sistemleri, farklı bir zamanlama algoritma kullanmayı seçebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Parçacıkları ve İş Parçacığı Oluşturmayı Kullanma](../../../docs/standard/threading/using-threads-and-threading.md)
- [Windows'ta Yönetilen ve Yönetilmeyen İş Parçacığı Oluşturma](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)
