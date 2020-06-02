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
ms.openlocfilehash: 369631603791d90c51244c1dc9907b9d8ec17364
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291168"
---
# <a name="pausing-and-interrupting-threads"></a>İş parçacıklarını duraklatma ve kesintiye uğratma

İş parçacıklarının etkinliklerini eşitlemeen yaygın yolları, iş parçacıklarını engellemek ve yayınlamak ya da nesnelerin veya kod bölgelerini kilitlemek için kullanılır. Bu kilitleme ve engelleme mekanizmaları hakkında daha fazla bilgi için bkz. [eşitleme temel bilgilerine genel bakış](overview-of-synchronization-primitives.md).  
  
 Ayrıca, iş parçacıklarından uyumayı koyabilirsiniz. İş parçacıkları engellendiğinde veya uyurken, <xref:System.Threading.ThreadInterruptedException> bunları bekleme durumlarından ayırmak için kullanabilirsiniz.  
  
## <a name="the-threadsleep-method"></a>Thread. Sleep yöntemi

 Yöntemi çağırmak, <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> geçerli iş parçacığının, yönteme geçirdiğiniz süre veya zaman aralığı için hemen blok almasına neden olur ve zaman diliminin geri kalanını başka bir iş parçacığına verir. Bu Aralık sona erdiğinde, Uyuyan iş parçacığı yürütmeyi sürdürür.  
  
 Bir iş parçacığı <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> başka bir iş parçacığında çağrılamaz.  <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>, her zaman geçerli iş parçacığının uykuya geçmesine neden olan statik bir yöntemdir.  
  
 <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>Bir değeriyle çağırmak <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> , Uyuyan iş parçacığında yöntemi çağıran başka bir iş parçacığı tarafından kesintiye gelinceye kadar <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> veya yöntemine bir çağrı tarafından sonlandırılana kadar bir iş parçacığının uykuya geçmesini sağlar <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> .  Aşağıdaki örnekte, Uyuyan bir iş parçacığını kesintiye uğratma yöntemleri gösterilmektedir.  
  
 [!code-csharp[Conceptual.Threading.Resuming#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Threading.Resuming/cs/Sleep1.cs#1)]
 [!code-vb[Conceptual.Threading.Resuming#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Threading.Resuming/vb/Sleep1.vb#1)]  
  
## <a name="interrupting-threads"></a>İş parçacıklarını kesme

 Engellenen iş parçacığı üzerinde yöntemini çağırarak bekleyen bir iş parçacığını kesintiye getirebilirsiniz <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> <xref:System.Threading.ThreadInterruptedException> . Bu, iş parçacığını engelleme çağrısının dışına ayırır. İş parçacığı öğesini yakalamalı <xref:System.Threading.ThreadInterruptedException> ve çalışmaya devam etmek için uygun olan her şeyi yapması gerekir. İş parçacığı özel durumu yoksayarsa, çalışma zamanı özel durumu yakalar ve iş parçacığını sonlandırır.  
  
> [!NOTE]
> Çağrıldığında hedef iş parçacığı engellenmemişse <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> , iş parçacığı Engellene kadar kesintiye uğramaz. İş parçacığı hiçbir zaman engellerse, kesintiye uğramadan tamamlanmayacaktır.  
  
 Bir bekleme yönetilen bekleme ise, <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> ve <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> her ikisi de iş parçacığını hemen uyandırır. Bir bekleme, yönetilmeyen bir bekleme ise (örneğin, Win32 [WaitForSingleObject](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject) işlevi için bir platform çağırma çağrısı), <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> ya da yönetilen koda çağrı yapana kadar iş parçacığı denetimini ele geçirebilir. Yönetilen kodda, davranış aşağıdaki gibidir:  
  
- <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>bir iş parçacığını, içinde olabilecek herhangi bir bekleme durumundan uyandırır ve hedef iş parçacığında bir oluşturulmasına neden olur <xref:System.Threading.ThreadInterruptedException> .  
  
- <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>bir iş parçacığını herhangi bir bekleme durumundan uyandığında, iş parçacığında bir işlem oluşmasına neden olur <xref:System.Threading.ThreadAbortException> . Ayrıntılar için bkz. [Iş parçacıklarını yok](destroying-threads.md)etme.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadInterruptedException>
- <xref:System.Threading.ThreadAbortException>
- [İş Parçacığı Oluşturma](index.md)
- [Iş parçacıkları ve Iş parçacığı kullanma](using-threads-and-threading.md)
- [Eşitleme temelleri 'ne genel bakış](overview-of-synchronization-primitives.md)
