---
title: 'Nasıl yapılır: düşük düzeyli eşitleme için SpinLock kullanma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to use
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff604b94ecef1ffec5fe9845df7c5ba35f5857d7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934439"
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a>Nasıl yapılır: düşük düzeyli eşitleme için SpinLock kullanma

Aşağıdaki örnek nasıl kullanılacağını gösterir. bir <xref:System.Threading.SpinLock>. Bu örnekte, kritik bölüm için iyi bir aday hale getiren iş en az miktarda gerçekleştiren bir <xref:System.Threading.SpinLock>. Artan iş küçük bir miktar performansını artırır <xref:System.Threading.SpinLock> standart kilit karşılaştırılan. Bununla birlikte, başlangıçtan bir SpinLock standart bir kilit daha pahalı olur bir noktası yoktur. Kilit türü programınızdaki daha iyi performans sağlar görmek için profil oluşturma profil oluşturma araçlarındaki işlevselliği eşzamanlılık kullanabilirsiniz. Daha fazla bilgi için [eşzamanlılık görselleştiricisi](/visualstudio/profiling/concurrency-visualizer).  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <xref:System.Threading.SpinLock> Paylaşılan kaynakta kilit yönelik zaman yararlı olabileceği çok uzun. Bu gibi durumlarda, çok çekirdekli bilgisayarlarda, kilit yayımlanana kadar birkaç döngülerini dönmeye engellenmiş iş parçacığı için verimli olabilir. Dönen tarafından iş parçacığı, hangi CPU yoğunluklu bir işlemdir engellenmediğinden haline gelir. <xref:System.Threading.SpinLock> mantıksal işlemci veya Hyper-Threading sistemleriyle öncelik ters çevirmeyi engellenmiştir belirli koşullar altında dönen durdurur.  
  
 Bu örnekte <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> sınıfını kullanıcı eşitleme için çok iş parçacıklı erişimi gerektirir. .NET Framework sürüm 4'ü hedefleyen uygulamalar, başka bir seçenek kullanmaktır <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, kullanıcı kilitleri gerektirmez.  
  
 Kullanımına dikkat edin `false` (`False` Visual Basic'te) çağrısında <xref:System.Threading.SpinLock.Exit%2A?displayProperty=nameWithType>. Bu, en iyi performansı sağlar. Belirtin `true` (`True` Visual Basic'te) IA64 mimariler bellek sınırı kullanmak için hangi aktarır kilit çıkmak diğer iş parçacıkları için kullanılabilir olmasını sağlamak için yazma arabelleği.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş parçacığı nesneleri ve özellikleri](threading-objects-and-features.md)
- [lock deyimi (C#)](../../csharp/language-reference/keywords/lock-statement.md)
- [SyncLock deyimi (Visual Basic)](../../visual-basic/language-reference/statements/synclock-statement.md)
