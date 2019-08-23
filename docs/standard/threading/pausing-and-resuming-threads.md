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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3dcee9c45cdbf029ccba90a963c9cea0a9c7ad4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963573"
---
# <a name="pausing-and-interrupting-threads"></a>İş parçacıklarını duraklatma ve kesintiye uğratma

İş parçacıklarının etkinliklerini eşitlemeen yaygın yolları, iş parçacıklarını engellemek ve yayınlamak ya da nesnelerin veya kod bölgelerini kilitlemek için kullanılır. Bu kilitleme ve engelleme mekanizmaları hakkında daha fazla bilgi için bkz. [eşitleme temel bilgilerine genel bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Ayrıca, iş parçacıklarından uyumayı koyabilirsiniz. İş parçacıkları engellendiğinde veya uyurken, bunları bekleme durumlarından ayırmak <xref:System.Threading.ThreadInterruptedException> için kullanabilirsiniz.  
  
## <a name="the-threadsleep-method"></a>Thread. Sleep yöntemi

 <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> Yöntemi çağırmak, geçerli iş parçacığının, yönteme geçirdiğiniz süre veya zaman aralığı için hemen blok almasına neden olur ve zaman diliminin geri kalanını başka bir iş parçacığına verir. Bu Aralık sona erdiğinde, Uyuyan iş parçacığı yürütmeyi sürdürür.  
  
 Bir iş parçacığı başka <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> bir iş parçacığında çağrılamaz.  <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>, her zaman geçerli iş parçacığının uykuya geçmesine neden olan statik bir yöntemdir.  
  
 Bir <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> değeriyleçağırmak<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> , Uyuyan iş parçacığında yöntemi çağıran başka bir iş parçacığı tarafından kesintiye gelinceye kadar veya yöntemine bir çağrı tarafından sonlandırılana kadar bir iş parçacığının uykuya geçmesini sağlar.<xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType>  Aşağıdaki örnekte, Uyuyan bir iş parçacığını kesintiye uğratma yöntemleri gösterilmektedir.  
  
 [!code-csharp[Conceptual.Threading.Resuming#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Threading.Resuming/cs/Sleep1.cs#1)]
 [!code-vb[Conceptual.Threading.Resuming#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Threading.Resuming/vb/Sleep1.vb#1)]  
  
## <a name="interrupting-threads"></a>İş parçacıklarını kesme

 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> Engellenen<xref:System.Threading.ThreadInterruptedException>iş parçacığı üzerinde yöntemini çağırarak bekleyen bir iş parçacığını kesintiye getirebilirsiniz. Bu, iş parçacığını engelleme çağrısının dışına ayırır. İş parçacığı öğesini yakalamalı <xref:System.Threading.ThreadInterruptedException> ve çalışmaya devam etmek için uygun olan her şeyi yapması gerekir. İş parçacığı özel durumu yoksayarsa, çalışma zamanı özel durumu yakalar ve iş parçacığını sonlandırır.  
  
> [!NOTE]
> Çağrıldığında hedef iş parçacığı engellenmemişse <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> , iş parçacığı Engellene kadar kesintiye uğramaz. İş parçacığı hiçbir zaman engellerse, kesintiye uğramadan tamamlanmayacaktır.  
  
 Bir bekleme yönetilen bekleme ise, <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> ve <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> her ikisi de iş parçacığını hemen uyandırır. Bir bekleme, yönetilmeyen bir bekleme ise (örneğin, Win32 [WaitForSingleObject](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject) işlevi için bir platform çağırma çağrısı), <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> ya da <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> yönetilen koda çağrı yapana kadar iş parçacığı denetimini ele geçirebilir. Yönetilen kodda, davranış aşağıdaki gibidir:  
  
- <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>bir iş parçacığını, içinde olabilecek herhangi bir bekleme durumundan uyandırır ve hedef <xref:System.Threading.ThreadInterruptedException> iş parçacığında bir oluşturulmasına neden olur.  
  
- <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>bir iş parçacığını herhangi bir bekleme durumundan uyandığında, iş parçacığında bir <xref:System.Threading.ThreadAbortException> işlem oluşmasına neden olur. Ayrıntılar için bkz. [Iş parçacıklarını yok](../../../docs/standard/threading/destroying-threads.md)etme.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadInterruptedException>
- <xref:System.Threading.ThreadAbortException>
- [İş parçacığı oluşturma](../../../docs/standard/threading/index.md)
- [İş Parçacıkları ve İş Parçacığı Oluşturmayı Kullanma](../../../docs/standard/threading/using-threads-and-threading.md)
- [Eşitleme Temellerine Genel Bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
