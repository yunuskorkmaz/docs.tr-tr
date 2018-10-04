---
title: Duraklatma ve iş parçacıkları kesme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interrupting threads
- threading [.NET Framework], pausing
- pausing threads
ms.assetid: 9fce4859-a19d-4506-b082-7dd0792688ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b66881a8a42c0c34b5c2119f7404fe7787c8f3f2
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48779588"
---
# <a name="pausing-and-interrupting-threads"></a>Duraklatma ve iş parçacıkları kesme

İş parçacığı etkinlikleri eşitlemek için en yaygın yollarından bloğu ve yayın iş parçacıkları veya nesneleri Kilitle veya bölgeleri olabilir. Bu kilitleme ve mekanizmaları engelleme hakkında daha fazla bilgi için bkz. [eşitleme temellerine genel bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 İş parçacıkları kendilerini uyku moduna yerleştirmek de olabilir. İş parçacığı engellendi veya kullanabileceğiniz uyku, ne zaman bir <xref:System.Threading.ThreadInterruptedException> bekleme durumlarını dışında bölüneceği.  
  
## <a name="the-threadsleep-method"></a>Net_thread_sleep yöntemi

 Çağırma <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> yöntemi milisaniye veya yönteme için zaman aralığı için hemen engellemek geçerli iş parçacığının neden olur ve kendi zaman dilimi başka bir iş parçacığına geri kalanı verir. Uykudaki iş parçacığı bu aralığı sona erdiğinde sonra yürütmeye devam eder.  
  
 Bir iş parçacığı çağıramaz <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> başka bir iş parçacığı üzerinde.  <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> her zaman geçerli iş parçacığı uyku durumuna neden olan statik bir yöntemdir.  
  
 Çağırma <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> değeriyle <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> çağıran başka bir iş parçacığı tarafından kesintiye kadar beklenecek bir iş parçacığı neden <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> yöntemi uykudaki iş parçacığı veya bir çağrı tarafından sonlandırılır kadar kendi <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> yöntemi.  Aşağıdaki örnek, Uyuyan bir iş parçacığını engellemeden hem yöntemleri gösterir.  
  
 [!code-csharp[Conceptual.Threading.Resuming#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Threading.Resuming/cs/Sleep1.cs#1)]
 [!code-vb[Conceptual.Threading.Resuming#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Threading.Resuming/vb/Sleep1.vb#1)]  
  
## <a name="interrupting-threads"></a>İş parçacıkları kesme

 Bekleyen iş parçacığı çağırarak engelleyebilecek <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> atmak için engellenen iş parçacığı üzerinde yöntemini bir <xref:System.Threading.ThreadInterruptedException>, iş parçacığı engelleme çağrısının dışına keser. İş parçacığı yakalamalısınız <xref:System.Threading.ThreadInterruptedException> ve her çalışmaya devam etmek uygundur. İş parçacığı özel durumu yoksayar, çalışma zamanı özel durumu yakalar ve iş parçacığını durdurur.  
  
> [!NOTE]
>  Hedef iş parçacığı değilse ne zaman engellenen <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> olan çağrılır, iş parçacığı kadar blokları kesintiye uğramaz. Hiçbir zaman iş parçacığını engeller, hiç kesintiye olmadan tamamlayabilirsiniz.  
  
 Bekleme yönetilen bir bekleme ise <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> ve <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> hem de iş parçacığı hemen Uyandırma. Yönetilmeyen bir bekleme bekleme ise (örneğin, bir platform çağırma çağrısı Win32 [WaitForSingleObject](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject) işlevi), hiçbiri <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> ya da <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> kadar döndürür veya yönetilen koda çağıran iş parçacığının denetimini ele geçirebilir. Yönetilen kodda davranış aşağıdaki gibidir:  
  
-   <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> bir iş parçacığı dışında olabilir ve neden olan herhangi bir bekleme modundan bir <xref:System.Threading.ThreadInterruptedException> hedef iş parçacığında için.  
  
-   <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> bir iş parçacığı dışında olabilir ve neden olan herhangi bir bekleme modundan bir <xref:System.Threading.ThreadAbortException> iş parçacığında harekete geçirilmesine. Ayrıntılar için bkz [iş parçacıklarını yok etme](../../../docs/standard/threading/destroying-threads.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Thread>  
- <xref:System.Threading.ThreadInterruptedException>  
- <xref:System.Threading.ThreadAbortException>  
- [İş parçacığı oluşturma](../../../docs/standard/threading/index.md)  
- [İş Parçacıkları ve İş Parçacığı Oluşturmayı Kullanma](../../../docs/standard/threading/using-threads-and-threading.md)  
- [Eşitleme Temellerine Genel Bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
