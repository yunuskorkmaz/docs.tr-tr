---
title: "İş Parçacıklarını Zamanlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], scheduling
- scheduling threads
ms.assetid: 67e4a0eb-3095-4ea7-b20f-908faa476277
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6bb715c11cc0d9b07e4ea8805ace7680ca92097c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="scheduling-threads"></a>İş Parçacıklarını Zamanlama
Her iş parçacığı kendisine atanmış bir iş parçacığı önceliği vardır. Ortak dil çalışma zamanı içinde oluşturulan iş parçacığı başlangıçta önceliğini atanan **ThreadPriority.Normal**. Çalışma zamanı dışında oluşturulan iş parçacıklarını yönetilen ortam girilen önce sahip oldukları öncelik korur. Almak veya herhangi bir iş parçacığı ile önceliğini ayarlamak **Thread.Priority** özelliği.  
  
 İş parçacığı kendi önceliği temelinde yürütme için zamanlanır. İş parçacığı içinde çalışma zamanı yürütme olsa bile, tüm iş parçacıklarının işlemci zaman dilimi işletim sistemi tarafından atanır. İş parçacığı yürütüldüğü sırayı belirlemek için kullanılan zamanlama algoritması ayrıntılarını her işletim sistemiyle değişir. Bazı işletim sistemlerinde iş parçacığı yüksek önceliği (yürütülebilir. Bu iş parçacıkları) ile her zaman ilk çalışacak şekilde zamanlanır. Birden çok iş parçacığı aynı önceliğe sahip iş parçacıklarının her iş parçacığı yürütme sabit bir zaman dilimi vererek, bu öncelikle Zamanlayıcı dolaşma tüm varsa. Yüksek bir önceliği olan bir iş parçacığı çalıştırmak için kullanılabilir olduğu sürece, daha düşük öncelikli iş parçacıklarının yürütmek almamış. Belirli bir öncelikte artık runnable iş parçacığı olduğunda Zamanlayıcı sonraki düşük önceliği taşır ve iş parçacığı yürütmesi için öncelikle zamanlar. Daha yüksek bir öncelik iş parçacığı runnable olursa, daha düşük öncelikli işler için iş parçacığı etkisiz ve daha yüksek öncelik iş parçacığı bir kez daha yürütmeye izin. Bir uygulamanın kullanıcı arabiriminde ön ve arka plan arasında taşındıkça tüm, en üstünde, işletim sistemini de iş parçacığı öncelikleri dinamik olarak ayarlayabilirsiniz. Diğer işletim sistemleri, farklı bir zamanlama algoritmasıdır kullanmayı seçebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş Parçacıkları ve İş Parçacığı Oluşturmayı Kullanma](../../../docs/standard/threading/using-threads-and-threading.md)  
 [Windows'ta Yönetilen ve Yönetilmeyen İş Parçacığı Oluşturma](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)
