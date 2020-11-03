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
ms.openlocfilehash: 3fb19c2b36d97710685cac4ecd10f47a119814ce
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93189192"
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a>Nasıl yapılır: alt düzey eşitleme için SpinLock kullanma

Aşağıdaki örnek, ' nin nasıl kullanılacağını göstermektedir <xref:System.Threading.SpinLock> . Bu örnekte kritik bölüm, bir için iyi bir aday olan en az miktarda iş gerçekleştirir <xref:System.Threading.SpinLock> . Çalışmanın artırılması küçük bir süre, standart bir kilit ile karşılaştırıldığında performansını artırır <xref:System.Threading.SpinLock> . Ancak, bir SpinLock 'un standart kilitten daha pahalı hale geldiği bir nokta vardır. Hangi tür kilit türünün programınızda daha iyi performans sağladığını görmek için profil oluşturma araçlarında eşzamanlılık profil oluşturma işlevini kullanabilirsiniz. Daha fazla bilgi için bkz. [Eşzamanlılık görselleştiricisi](/visualstudio/profiling/concurrency-visualizer).  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <xref:System.Threading.SpinLock> Paylaşılan bir kaynaktaki kilit çok uzun süre tutulmadığında faydalı olabilir. Bu gibi durumlarda, çok çekirdekli bilgisayarlarda, kilit serbest bırakılana kadar engellenen iş parçacığının birkaç döngü için dönmesi verimli olabilir. Dönen iş parçacığı, CPU yoğun bir işlem olan engellenmez. <xref:System.Threading.SpinLock> , Hyper-Threading ile sistemlerdeki mantıksal işlemcilerin veya öncelikli olmayan koşullarda oluşan sorunları engellemek için belirli koşullar altında dönmesini durdurur.  
  
 Bu örnek <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> , çok iş parçacıklı erişim için Kullanıcı eşitlemesi gerektiren sınıfını kullanır. Başka bir seçenek de, <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> Kullanıcı kilitleri gerektirmeyen öğesini kullanmaktır.  
  
 Çağrısında öğesinin kullanımını aklınızda edin `false` <xref:System.Threading.SpinLock.Exit%2A?displayProperty=nameWithType> . Bu, en iyi performansı sağlar. `true`Kilit, diğer iş parçacıklarının çıkış için artık kullanılabilir olduğundan emin olmak için yazma arabelleğini temizleyecek bellek dilimini kullanmak üzere IA64 mimarilerinde belirtin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş parçacığı nesneleri ve özellikleri](threading-objects-and-features.md)
- [Lock deyimleri (C#)](../../csharp/language-reference/keywords/lock-statement.md)
- [SyncLock ekstresi (Visual Basic)](../../visual-basic/language-reference/statements/synclock-statement.md)
