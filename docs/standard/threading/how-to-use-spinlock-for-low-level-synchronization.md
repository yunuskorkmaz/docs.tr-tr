---
title: "Nasıl kullanılır: düşük seviyeli senkronizasyon için SpinLock'u kullanın"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to use
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
ms.openlocfilehash: ad254cb6208bff868e5fc689c502b7ddcc175ad5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73137961"
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a>Nasıl kullanılır: düşük seviyeli senkronizasyon için SpinLock'u kullanın

Aşağıdaki örnek, bir <xref:System.Threading.SpinLock>. Bu örnekte, kritik bölüm en az miktarda iş gerçekleştirir, bu <xref:System.Threading.SpinLock>da onu bir . İşi küçük bir miktar artırmak, <xref:System.Threading.SpinLock> standart bir kilitle karşılaştırıldığında performansı artırır. Ancak, bir SpinLock standart bir kilit daha pahalı hale gelir bir nokta vardır. Hangi kilit türünün programınızda daha iyi performans sağladığını görmek için profil oluşturma araçlarındaki eşzamanlılık profil oluşturma işlevini kullanabilirsiniz. Daha fazla bilgi için [Concurrency Visualizer'a](/visualstudio/profiling/concurrency-visualizer)bakın.  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <xref:System.Threading.SpinLock>paylaşılan bir kaynağa kilitlenme çok uzun süre tutulmadığında yararlı olabilir. Bu gibi durumlarda, çok çekirdekli bilgisayarlarda, kilit serbest bırakılıncaya kadar engellenen iş parçacığının birkaç döngü boyunca dönmesi verimli olabilir. Döndürülerek, iş parçacığı engellenmez, cpu yoğun bir işlemdir. <xref:System.Threading.SpinLock>Hiper-Threading ile sistemlerde mantıksal işlemcilerin açlığını veya öncelikli ters çevirmeyi önlemek için belirli koşullar altında dönmeyi durdurur.  
  
 Bu örnek, <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> çok iş parçacığı erişimi için kullanıcı eşitleme gerektiren sınıf kullanır. .NET Framework sürüm 4'nü hedefleyen uygulamalarda, başka <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>bir seçenek de kullanıcı kilitleri gerektirmeyen bir seçenek kullanmaktır.  
  
 `false` (Visual`False` Basic'te) 'nin ' <xref:System.Threading.SpinLock.Exit%2A?displayProperty=nameWithType>için yapılan çağrıda kullanımına dikkat edin. Bu en iyi performansı sağlar. `true` IA64 mimarilerinde (Visual`True` Basic'te) kilitartık diğer iş parçacıkları için kullanılabilir olduğundan emin olmak için yazma arabellekleri temizler bellek çit, kullanmak için belirtin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş parçacığı nesneleri ve özellikleri](threading-objects-and-features.md)
- [kilit deyimi (C#)](../../csharp/language-reference/keywords/lock-statement.md)
- [SyncLock deyimi (Visual Basic)](../../visual-basic/language-reference/statements/synclock-statement.md)
