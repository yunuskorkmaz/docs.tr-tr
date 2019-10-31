---
title: 'Nasıl yapılır: alt düzey eşitleme için SpinLock kullanma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to use
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
ms.openlocfilehash: ad254cb6208bff868e5fc689c502b7ddcc175ad5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137961"
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a>Nasıl yapılır: alt düzey eşitleme için SpinLock kullanma

Aşağıdaki örnek, bir <xref:System.Threading.SpinLock>nasıl kullanacağınızı gösterir. Bu örnekte, kritik bölüm, <xref:System.Threading.SpinLock>için iyi bir aday sağlayan en az miktarda iş gerçekleştirir. Çalışmanın artırılması küçük miktarda, standart bir kilit ile karşılaştırıldığında <xref:System.Threading.SpinLock> performansını arttırır. Ancak, bir SpinLock 'un standart kilitten daha pahalı hale geldiği bir nokta vardır. Hangi tür kilit türünün programınızda daha iyi performans sağladığını görmek için profil oluşturma araçlarında eşzamanlılık profil oluşturma işlevini kullanabilirsiniz. Daha fazla bilgi için bkz. [Eşzamanlılık görselleştiricisi](/visualstudio/profiling/concurrency-visualizer).  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <xref:System.Threading.SpinLock> paylaşılan bir kaynaktaki kilit çok uzun süre tutulmadığında yararlı olabilir. Bu gibi durumlarda, çok çekirdekli bilgisayarlarda, kilit serbest bırakılana kadar engellenen iş parçacığının birkaç döngü için dönmesi verimli olabilir. Dönen iş parçacığı, CPU yoğun bir işlem olan engellenmez. <xref:System.Threading.SpinLock>, Hyper-Threading ile sistemlerdeki mantıksal işlemcilerin veya öncelikli bir sürüm olmadığından emin olmak için belirli koşullarda dönmesini durdurur.  
  
 Bu örnek, çok iş parçacıklı erişim için Kullanıcı eşitlemesi gerektiren <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> sınıfını kullanır. .NET Framework sürüm 4 ' ü hedefleyen uygulamalarda, başka bir seçenek, herhangi bir Kullanıcı kilidi gerektirmeyen <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>kullanmaktır.  
  
 <xref:System.Threading.SpinLock.Exit%2A?displayProperty=nameWithType>çağrısında `false` (Visual Basic`False`) kullanımını göz önünde edin. Bu, en iyi performansı sağlar. Kilit, diğer iş parçacıklarının çıkış için kullanılabilir durumda olduğundan emin olmak için, yazma arabelleğini boşaltan bir bellek dilimini kullanmak üzere ıA64 mimarilerinde `true` (Visual Basic`True`) belirtin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş parçacığı nesneleri ve özellikleri](threading-objects-and-features.md)
- [Lock deyimleri (C#)](../../csharp/language-reference/keywords/lock-statement.md)
- [SyncLock ekstresi (Visual Basic)](../../visual-basic/language-reference/statements/synclock-statement.md)
