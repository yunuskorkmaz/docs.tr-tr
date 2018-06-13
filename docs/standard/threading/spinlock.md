---
title: SpinLock
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization primitives, SpinLock
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7d1d95030d2bc9f9288ae134471c150a37291b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582265"
---
# <a name="spinlock"></a>SpinLock
<xref:System.Threading.SpinLock> Bir kilidi beklerken dönerek bir alt düzey, karşılıklı dışlama eşitleme ilkel yapısıdır. Bekleme süresini kısa ve çakışma en az olduğunda olması beklenen zaman çok çekirdekli bilgisayarlarda <xref:System.Threading.SpinLock> kilitleri diğer tür daha iyi gerçekleştirebilirsiniz. Ancak, kullanmanızı öneririz <xref:System.Threading.SpinLock> yalnızca zaman, profil oluşturma saptamanıza <xref:System.Threading.Monitor?displayProperty=nameWithType> yöntemi veya <xref:System.Threading.Interlocked> yöntemleri önemli ölçüde performans programınızın yavaşlamasının.  
  
 <xref:System.Threading.SpinLock> Bunu henüz kilidi ele geçirmiş değil olsa bile iş parçacığının zaman dilimi verim. İş parçacığı önceliği ters çevirmeyi önlemek için ve ilerleme atık toplayıcı etkinleştirmek için bunu yapar. Kullandığınızda, bir <xref:System.Threading.SpinLock>, birden çok çok kısa bir süre için hiçbir iş parçacığı kilidi tutabilir ve kilidi tutan sırada hiçbir iş parçacığı engelleyebilirsiniz emin olun.  
  
 SpinLock bir değer türü olduğundan, aynı kilit başvurmak için iki kopya düşünüyorsanız açıkça başvuruya göre geçirdiğiniz gerekir.  
  
 Bu tür kullanma hakkında daha fazla bilgi için bkz: <xref:System.Threading.SpinLock?displayProperty=nameWithType>. Bir örnek için bkz: [nasıl yapılır: alt düzey eşitleme için SpinLock kullanma](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md).  
  
 <xref:System.Threading.SpinLock> destekleyen bir *iş parçacığı*-*izleme* geliştirme aşaması boyunca belirli bir zamanda kilit iş parçacığı izlemenize yardımcı olması için kullanabileceğiniz modu. İş parçacığı izleme modunu hata ayıklama için faydalıdır, ancak performans azaltabileceğinden, programınızın yayın sürümünü kapatmak olmasını öneririz. Daha fazla bilgi için bkz: [nasıl yapılır: spinlock'ta etkinleştirmek iş parçacığı izleme modunu](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş Parçacığı Nesneleri ve Özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)
