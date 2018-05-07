---
title: İş Parçacıklarını Duraklatma ve Sürdürme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resuming threads
- threading [.NET Framework], pausing
- pausing threads
ms.assetid: 9fce4859-a19d-4506-b082-7dd0792688ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9c2d58576098c83af110f2a713a0a8562e23aec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="pausing-and-resuming-threads"></a>İş Parçacıklarını Duraklatma ve Sürdürme
İş parçacığı etkinliklerini eşitlemek için en yaygın blok ve yayın iş parçacığı veya kilidi nesneleri veya kod bölümlerinin yollarıdır. Bu kilitleme ve mekanizmaları engelleme hakkında daha fazla bilgi için bkz: [eşitleme temellerine genel bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 İş parçacığı kendilerini uyku moduna yerleştirmek de olabilir. Ne zaman iş parçacığı engellendi veya kullanabileceğiniz uyku, bir <xref:System.Threading.ThreadInterruptedException> bekleme durumlarını dışında ayırmak için.  
  
## <a name="the-threadsleep-method"></a>Thread.Sleep yöntemi  
 Çağırma <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> yöntemi milisaniye veya yöntemine geçirdiğiniz zaman aralığı sayısı hemen engellemek geçerli iş parçacığının neden olur ve başka bir iş parçacığı için kendi zaman dilimi kalanı verir. Bu aralığı geçtikten sonra Uyuyan iş parçacığı yürütme devam ettirir.  
  
 Bir iş parçacığı çağıramaz <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> başka bir iş parçacığı üzerinde.  <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> her zaman uyku moduna geçerli iş parçacığının neden statik bir yöntemdir.  
  
 Çağırma <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> değerini <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> çağıran başka bir iş parçacığı tarafından kesilene kadar uyku için bir iş parçacığı neden <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> yöntemi Uyuyan iş parçacığı üzerinde veya bir çağrı tarafından durduruluncaya kadar kendi <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> yöntemi.  Aşağıdaki örnek Uyuyan bir iş parçacığı kesintiye hem yöntemleri gösterilmektedir.  
  
 [!code-csharp[Conceptual.Threading.Resuming#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Threading.Resuming/cs/Sleep1.cs#1)]
 [!code-vb[Conceptual.Threading.Resuming#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Threading.Resuming/vb/Sleep1.vb#1)]  
  
## <a name="interrupting-threads"></a>İş parçacığı kesintiye  
 Çağırarak bekleyen iş parçacığı kesintiye uğratabilir <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> yöntemi atmak için engellenmiş iş parçacığı üzerinde bir <xref:System.Threading.ThreadInterruptedException>, iş parçacığı engelleme çağrısı dışında keser. İş parçacığı catch <xref:System.Threading.ThreadInterruptedException> ve ne olursa olsun çalışmaya devam etmek uygundur. Özel iş parçacığı yoksayar, çalışma zamanı özel durumu yakalar ve iş parçacığı durdurur.  
  
> [!NOTE]
>  Hedef iş parçacığı değilse ne zaman engellenen <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> olduğu olarak adlandırılan, iş parçacığı kadar blokları kesintiye uğramaz. İş parçacığı hiçbir zaman engelliyorsa hiç kesintiye olmadan işlemini tamamlayamadı.  
  
 Bekleme yönetilen bekleyin, sonra ise <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> ve <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> hem de iş parçacığı hemen Uyandırma. Bekleme yönetilmeyen bekleme ise (örneğin, bir platform çağırma çağrısı Win32 [WaitForSingleObject](https://msdn.microsoft.com/library/windows/desktop/ms687032\(v=vs.85\).aspx) işlevi), hiçbiri <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> ya da <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> döndürür veya yönetilen koda çağrı kadar iş parçacığı denetimini ele geçirebilir. Yönetilen kodda davranış aşağıdaki gibidir:  
  
-   <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> bir iş parçacığı dışında olabilir ve neden olan tüm bekleme modundan bir <xref:System.Threading.ThreadInterruptedException> hedef iş parçacığında durum için.  
  
-   <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> bir iş parçacığı dışında olabilir ve neden olan tüm bekleme modundan bir <xref:System.Threading.ThreadAbortException> iş parçacığı üzerinde durum için. Ayrıntılar için bkz [iş parçacıklarını yok etme](../../../docs/standard/threading/destroying-threads.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadInterruptedException>  
 <xref:System.Threading.ThreadAbortException>  
 [İş parçacığı oluşturma](../../../docs/standard/threading/index.md)  
 [İş Parçacıkları ve İş Parçacığı Oluşturmayı Kullanma](../../../docs/standard/threading/using-threads-and-threading.md)  
 [Eşitleme Temellerine Genel Bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
