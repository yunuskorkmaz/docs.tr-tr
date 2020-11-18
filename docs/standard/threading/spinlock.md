---
title: SpinLock
ms.date: 03/30/2017
helpviewer_keywords:
- synchronization primitives, SpinLock
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
ms.openlocfilehash: 071bde6e8b32d5712256e24c83d713cd63f2bffb
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94819012"
---
# <a name="spinlock"></a>SpinLock
<xref:System.Threading.SpinLock>Yapı, bir kilit elde etmek için beklerken dönerek bir alt düzey, karşılıklı dışlama eşitleme temel lamasıdır. Çok sayıda bilgisayarda, bekleme sürelerinin kısa olması beklendiğinde ve çekişme en az olduğunda, <xref:System.Threading.SpinLock> diğer tür kilitleri daha iyi gerçekleştirebilir. Bununla birlikte, <xref:System.Threading.SpinLock> yalnızca <xref:System.Threading.Monitor?displayProperty=nameWithType> yöntemin veya <xref:System.Threading.Interlocked> yöntemlerin, programınızın performansını önemli ölçüde yavaşlattığı profil oluşturarak bunu kullanmanızı öneririz.  
  
 <xref:System.Threading.SpinLock> , henüz kilidi almış olmasa bile iş parçacığının zaman dilimini alabilir. Bu, iş parçacığı öncelikli olmayan sürümden kaçınmak ve çöp toplayıcısının ilerleme durumuna uğramasını etkinleştirmek için bunu yapar. <xref:System.Threading.SpinLock>' I kullandığınızda, hiçbir iş parçacığının çok kısa bir zaman dilimi için kilidi tutamadığından ve kilidi tutarken hiçbir iş parçacığının engelleyebileceğinden emin olun.  
  
 SpinLock bir değer türü olduğundan, iki kopyayı aynı kiline başvuracak şekilde düşünüyorsanız başvuruya göre açıkça geçirmeniz gerekir.  
  
 Bu türü kullanma hakkında daha fazla bilgi için bkz <xref:System.Threading.SpinLock?displayProperty=nameWithType> .. Bir örnek için bkz. [nasıl yapılır: Low-Level eşitleme Için SpinLock kullanma](how-to-use-spinlock-for-low-level-synchronization.md).  
  
 <xref:System.Threading.SpinLock>*thread* - , kilidi belirli bir zamanda tutan iş parçacığını izlemeye yardımcı olmak için geliştirme aşamasında kullanabileceğiniz bir iş parçacığı *izleme* modunu destekler. İş parçacığı izleme modu hata ayıklama için çok faydalı olmakla kalmaz, performansı yavaşlatabilecek için programınızın yayın sürümünde kapatmanız önerilir. Daha fazla bilgi için bkz. [nasıl yapılır: SpinLock 'ta Thread-Tracking modunu etkinleştirme](how-to-enable-thread-tracking-mode-in-spinlock.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş parçacığı nesneleri ve özellikleri](threading-objects-and-features.md)
