---
title: SpinLock
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization primitives, SpinLock
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5bd2468c7b68a9c79e7418a32294676fb468e1a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62015063"
---
# <a name="spinlock"></a>SpinLock
<xref:System.Threading.SpinLock> Kilit beklerken dönerek bir alt düzey, karşılıklı dışlama eşitleme temel öğesi yapısıdır. Bekleme süresini kısa ve Çekişme en az olduğunda olması bekleniyor, çok çekirdekli bilgisayarlarda <xref:System.Threading.SpinLock> kilitleri diğer tür daha iyi gerçekleştirebilirsiniz. Ancak, kullanmanızı öneririz <xref:System.Threading.SpinLock> yalnızca zaman, profil oluşturma belirlediğiniz <xref:System.Threading.Monitor?displayProperty=nameWithType> yöntemi veya <xref:System.Threading.Interlocked> yöntemleri önemli ölçüde performans programınızın yavaşlatmasını.  
  
 <xref:System.Threading.SpinLock> iş parçacığının zaman dilimi getirilmesine neden bile, henüz bir kilit alınmadığı değil. İş parçacığı önceliği tersine çevirme önlemek ve ilerleme çöp toplayıcı etkinleştirmek için bunu yapar. Kullandığınızda, bir <xref:System.Threading.SpinLock>, birden çok çok kısa bir süre için hiçbir iş parçacığı kilit barındırabilir ve kilidini tutan sırada hiçbir iş parçacığını engelleyebildiğinden emin olun.  
  
 SpinLock bir değer türü olduğundan, aynı kilidi için başvuruda bulunmak için iki kopya düşünüyorsanız, açıkça, başvuruya göre geçmesi gerekir.  
  
 Bu tür kullanma hakkında daha fazla bilgi için bkz. <xref:System.Threading.SpinLock?displayProperty=nameWithType>. Bir örnek için bkz [nasıl yapılır: Düşük düzeyli eşitleme için SpinLock kullanma](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md).  
  
 <xref:System.Threading.SpinLock> destekleyen bir *iş parçacığı*-*izleme* geliştirme aşamasında belirli bir zamanda bir kilit iş parçacığı izlenmesine yardımcı olması için kullanabileceğiniz modu. İş parçacığı izleme modunu hata ayıklama için çok kullanışlıdır ancak performansı azaltabileceğinden, programınızı yayın sürümünde kapatmak olmasını öneririz. Daha fazla bilgi için [nasıl yapılır: Spinlock'ta iş parçacığı izleme modunu etkinleştirme](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Parçacığı Nesneleri ve Özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)
