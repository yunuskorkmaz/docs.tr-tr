---
title: SpinLock
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization primitives, SpinLock
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
ms.openlocfilehash: eac9a1be38ea81e8ccee1d05d9061ceeb597627f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73106165"
---
# <a name="spinlock"></a>SpinLock
Yapı, <xref:System.Threading.SpinLock> kilit elde etmek için beklerken dönen düşük seviyeli, karşılıklı dışlama senkronizasyonu ilkeldir. Çok çekirdekli bilgisayarlarda, bekleme sürelerinin kısa olması beklendiği <xref:System.Threading.SpinLock> ve çekişmenin en az olduğu zamanlarda, diğer kilit türlerine göre daha iyi performans gösterebilirsiniz. Ancak, yalnızca <xref:System.Threading.SpinLock> <xref:System.Threading.Monitor?displayProperty=nameWithType> yöntemin veya yöntemlerin <xref:System.Threading.Interlocked> programınızın performansını önemli ölçüde yavaşlattığını profil oluşturarak belirlerken kullanmanızı öneririz.  
  
 <xref:System.Threading.SpinLock>kilidi henüz edinmemiş olsa bile iş parçacığının zaman dilimini verebilir. Bunu, iş parçacığı öncelikli ters çevirmeyi önlemek ve çöp toplayıcısının ilerleme kaydetmesini sağlamak için yapar. Bir <xref:System.Threading.SpinLock>, hiçbir iş parçacığı çok kısa bir süre daha fazla kilidi tutamaz ve hiçbir iş parçacığı kilidi tutarken engelleyebilir emin olun.  
  
 SpinLock bir değer türü olduğundan, iki kopyanın aynı kilitle ifade etmesini istiyorsanız, bunu açıkça referans olarak geçirmeniz gerekir.  
  
 Bu tür nasıl kullanılacağı hakkında daha <xref:System.Threading.SpinLock?displayProperty=nameWithType>fazla bilgi için bkz. Örneğin, [bkz.](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md)  
  
 <xref:System.Threading.SpinLock>kilidi belirli bir zamanda tutan iş parçacığının izlenmesine yardımcı olmak için geliştirme aşamasında kullanabileceğiniz bir *iş parçacığı*-*izleme* modunu destekler. İş parçacığı izleme modu hata ayıklama için çok yararlıdır, ancak performansı yavaşlatabileceğinden programınızın sürüm sürümünde kapatmanızı öneririz. Daha fazla bilgi için [bkz: SpinLock'ta İş Parçacığı İzleme Modunu Etkinleştir.](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Parçacığı Nesneleri ve Özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)
