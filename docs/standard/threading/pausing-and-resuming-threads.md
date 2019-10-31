---
title: İş parçacıklarını duraklatma ve kesintiye uğratma
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
ms.openlocfilehash: 3020694b93479d5f1d64d31c203f8fe033a10320
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128999"
---
# <a name="pausing-and-interrupting-threads"></a>İş parçacıklarını duraklatma ve kesintiye uğratma

İş parçacıklarının etkinliklerini eşitlemeen yaygın yolları, iş parçacıklarını engellemek ve yayınlamak ya da nesnelerin veya kod bölgelerini kilitlemek için kullanılır. Bu kilitleme ve engelleme mekanizmaları hakkında daha fazla bilgi için bkz. [eşitleme temel bilgilerine genel bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Ayrıca, iş parçacıklarından uyumayı koyabilirsiniz. İş parçacıkları engellendiğinde veya uyurken, bunları bekleme durumlarından ayırmak için bir <xref:System.Threading.ThreadInterruptedException> kullanabilirsiniz.  
  
## <a name="the-threadsleep-method"></a>Thread. Sleep yöntemi

 <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> yöntemini çağırmak, geçerli iş parçacığının, yönteme geçirdiğiniz zaman aralığı veya zaman aralığı için hemen engellenmesine neden olur ve zaman diliminin geri kalanını başka bir iş parçacığına verir. Bu Aralık sona erdiğinde, Uyuyan iş parçacığı yürütmeyi sürdürür.  
  
 Bir iş parçacığı başka bir iş parçacığında <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> çağıramaz.  <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>, her zaman geçerli iş parçacığının uykuya geçmesine neden olan statik bir yöntemdir.  
  
 <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> bir <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> değeri ile çağırmak, uyku durumunda <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> yöntemini çağıran başka bir iş parçacığı tarafından kesintiye gelinceye kadar veya <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> yöntemine bir çağrı tarafından sonlandırılana kadar bir iş parçacığının uykuya geçmesini sağlar.  Aşağıdaki örnekte, Uyuyan bir iş parçacığını kesintiye uğratma yöntemleri gösterilmektedir.  
  
 [!code-csharp[Conceptual.Threading.Resuming#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Threading.Resuming/cs/Sleep1.cs#1)]
 [!code-vb[Conceptual.Threading.Resuming#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Threading.Resuming/vb/Sleep1.vb#1)]  
  
## <a name="interrupting-threads"></a>İş parçacıklarını kesme

 Bir <xref:System.Threading.ThreadInterruptedException>oluşturmak için engellenen iş parçacığı üzerinde <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> yöntemini çağırarak bekleyen bir iş parçacığını kesintiye getirebilirsiniz. Bu, iş parçacığını engelleme çağrısının dışına ayırır. İş parçacığı <xref:System.Threading.ThreadInterruptedException> yakalamalı ve çalışmaya devam etmek için uygun olan her şeyi yapabilmelidir. İş parçacığı özel durumu yoksayarsa, çalışma zamanı özel durumu yakalar ve iş parçacığını sonlandırır.  
  
> [!NOTE]
> <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> çağrıldığında hedef iş parçacığı engellenmemişse, iş parçacığı Engellene kadar kesintiye uğramaz. İş parçacığı hiçbir zaman engellerse, kesintiye uğramadan tamamlanmayacaktır.  
  
 Bir bekleme yönetilen bekleme ise, <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> ve <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> her ikisi de iş parçacığını hemen uyandırır. Bir bekleme, yönetilmeyen bir bekleme ise (örneğin, Win32 [WaitForSingleObject](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject) işlevine platform çağırma çağrısı), ne <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> ne de <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>, yönetilen koda geri dönene veya bir çağrı yapana kadar iş parçacığı denetimini ele geçirebilir. Yönetilen kodda, davranış aşağıdaki gibidir:  
  
- <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>, bir iş parçacığını bir bekleme modundan uyandırır ve hedef iş parçacığında bir <xref:System.Threading.ThreadInterruptedException> oluşturulmasına neden olur.  
  
- <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>, bir iş parçacığını bir bekleme modundan uyandırır ve iş parçacığında bir <xref:System.Threading.ThreadAbortException> oluşturulmasına neden olur. Ayrıntılar için bkz. [Iş parçacıklarını yok](../../../docs/standard/threading/destroying-threads.md)etme.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadInterruptedException>
- <xref:System.Threading.ThreadAbortException>
- [İş parçacığı oluşturma](../../../docs/standard/threading/index.md)
- [İş Parçacıkları ve İş Parçacığı Oluşturmayı Kullanma](../../../docs/standard/threading/using-threads-and-threading.md)
- [Eşitleme Temellerine Genel Bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
