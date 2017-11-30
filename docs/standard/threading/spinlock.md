---
title: SpinLock
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: synchronization primitives, SpinLock
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: efe9b3126b3c952ab156f9ca40752ad8d3fddcd1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="spinlock"></a>SpinLock
<xref:System.Threading.SpinLock> Bir kilidi beklerken dönerek bir alt düzey, karşılıklı dışlama eşitleme ilkel yapısıdır. Bekleme süresini kısa ve çakışma en az olduğunda olması beklenen zaman çok çekirdekli bilgisayarlarda <xref:System.Threading.SpinLock> kilitleri diğer tür daha iyi gerçekleştirebilirsiniz. Ancak, kullanmanızı öneririz <xref:System.Threading.SpinLock> yalnızca zaman, profil oluşturma saptamanıza <xref:System.Threading.Monitor?displayProperty=nameWithType> yöntemi veya <xref:System.Threading.Interlocked> yöntemleri önemli ölçüde performans programınızın yavaşlamasının.  
  
 <xref:System.Threading.SpinLock>Bunu henüz kilidi ele geçirmiş değil olsa bile iş parçacığının zaman dilimi verim. İş parçacığı önceliği ters çevirmeyi önlemek için ve ilerleme atık toplayıcı etkinleştirmek için bunu yapar. Kullandığınızda, bir <xref:System.Threading.SpinLock>, birden çok çok kısa bir süre için hiçbir iş parçacığı kilidi tutabilir ve kilidi tutan sırada hiçbir iş parçacığı engelleyebilirsiniz emin olun.  
  
 SpinLock bir değer türü olduğundan, aynı kilit başvurmak için iki kopya düşünüyorsanız açıkça başvuruya göre geçirdiğiniz gerekir.  
  
 Bu tür kullanma hakkında daha fazla bilgi için bkz: <xref:System.Threading.SpinLock?displayProperty=nameWithType>. Bir örnek için bkz: [nasıl yapılır: alt düzey eşitleme için SpinLock kullanma](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md).  
  
 <xref:System.Threading.SpinLock>destekleyen bir *iş parçacığı*-*izleme* geliştirme aşaması boyunca belirli bir zamanda kilit iş parçacığı izlemenize yardımcı olması için kullanabileceğiniz modu. İş parçacığı izleme modunu hata ayıklama için faydalıdır, ancak performans azaltabileceğinden, programınızın yayın sürümünü kapatmak olmasını öneririz. Daha fazla bilgi için bkz: [nasıl yapılır: spinlock'ta etkinleştirmek iş parçacığı izleme modunu](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş parçacığı nesneleri ve özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)
