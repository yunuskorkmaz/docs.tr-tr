---
title: SpinLock
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization primitives, SpinLock
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
ms.openlocfilehash: eac9a1be38ea81e8ccee1d05d9061ceeb597627f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73106165"
---
# <a name="spinlock"></a>SpinLock
<xref:System.Threading.SpinLock> yapısı, bir kilit elde etmek için beklerken dönerek bir alt düzey, karşılıklı dışlama eşitleme temel lamasıdır. Birden çok daha fazla bilgisayarda, bekleme sürelerinin kısa olması beklenen ve çekişme en az olduğunda <xref:System.Threading.SpinLock> diğer kilit türlerinden daha iyi bir performans sağlayabilir. Ancak, yalnızca <xref:System.Threading.Monitor?displayProperty=nameWithType> yönteminin veya <xref:System.Threading.Interlocked> yöntemlerinin, programınızın performansını önemli ölçüde yavaşlatıyor olduğunu profil oluşturarak <xref:System.Threading.SpinLock> kullanmanızı öneririz.  
  
 <xref:System.Threading.SpinLock>, henüz kilidi almış olmasa bile iş parçacığının zaman dilimini alabilir. Bu, iş parçacığı öncelikli olmayan sürümden kaçınmak ve çöp toplayıcısının ilerleme durumuna uğramasını etkinleştirmek için bunu yapar. <xref:System.Threading.SpinLock>kullandığınızda, hiçbir iş parçacığının çok kısa bir zaman dilimi için kilidi tutamadığından ve kilidi tutarken hiçbir iş parçacığının engelleyebileceğinden emin olun.  
  
 SpinLock bir değer türü olduğundan, iki kopyayı aynı kiline başvuracak şekilde düşünüyorsanız başvuruya göre açıkça geçirmeniz gerekir.  
  
 Bu türü kullanma hakkında daha fazla bilgi için bkz. <xref:System.Threading.SpinLock?displayProperty=nameWithType>. Bir örnek için bkz. [nasıl yapılır: alt düzey eşitleme Için SpinLock kullanma](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md).  
  
 <xref:System.Threading.SpinLock>, kilidi belirli bir zamanda tutan iş parçacığını izlemeye yardımcı olmak için geliştirme aşamasında kullanabileceğiniz bir *iş parçacığı*-*izleme* modunu destekler. İş parçacığı izleme modu hata ayıklama için çok faydalı olmakla kalmaz, performansı yavaşlatabilecek için programınızın yayın sürümünde kapatmanız önerilir. Daha fazla bilgi için bkz. [nasıl yapılır: sayaç Izleme modunu SpinLock 'Ta etkinleştirme](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Parçacığı Nesneleri ve Özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)
