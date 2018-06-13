---
title: 'Nasıl yapılır: Düşük Düzeyli Eşitleme için SpinLock Kullanma'
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
ms.openlocfilehash: 7795b25ca8e9337a53fc67ebc6f56130237d0764
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582762"
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a>Nasıl yapılır: Düşük Düzeyli Eşitleme için SpinLock Kullanma
Aşağıdaki örnekte nasıl kullanılacağını gösteren bir <xref:System.Threading.SpinLock>.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, en az miktarda iyi bir aday kolaylaştırır için iş kritik bölüm gerçekleştiren bir <xref:System.Threading.SpinLock>. İş artırılması küçük bir miktar performansını artırır <xref:System.Threading.SpinLock> standart kilit karşılaştırılan. Ancak bir SpinLock standart kilit daha pahalı hale noktası yoktur. Hangi tür kilit programınızdaki daha iyi performans sağlar görmek için profil oluşturma araçları işlevindeki profil eşzamanlılık kullanabilirsiniz. Daha fazla bilgi için bkz: [eşzamanlılık görselleştiricisi](/visualstudio/profiling/concurrency-visualizer).  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <xref:System.Threading.SpinLock> Paylaşılan bir kaynak üzerinde bir kilit için tutulması gonna yararlı olabilir çok uzun. Böyle durumlarda, çok çekirdekli bilgisayarlarda bu kilidi serbest kadar birkaç döngüsü boyunca dönmeye engellenmiş iş parçacığı için etkili olabilir. Dönen tarafından iş parçacığı, hangi CPU yoğunluklu bir işlemdir engellenmiş duruma değil. <xref:System.Threading.SpinLock> mantıksal işlemci veya Hyper-Threading sistemleriyle öncelik ters çevirmeyi engellenmiştir belirli koşullar altında dönen durdurur.  
  
 Bu örnekte <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> kullanıcı eşitleme için çok iş parçacıklı erişmesi sınıfı. .NET Framework sürüm 4 hedef uygulamalarda, başka bir seçenek kullanmaktır <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, kullanıcı kilitleri gerektirmez.  
  
 Kullanımına dikkat edin `false` (`False` Visual Basic'te) çağrısında <xref:System.Threading.SpinLock.Exit%2A>. Bu, en iyi performans sağlar. Belirtin `true` (`True`) bellek sınırı kullanmak için IA64 mimarileri üzerinde hangi boşaltır kilidi çıkmak başka bir iş parçacığı için kullanılabilir olduğundan emin olmak için yazma arabelleği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş Parçacığı Nesneleri ve Özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)
