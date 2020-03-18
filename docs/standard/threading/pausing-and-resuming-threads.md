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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73128999"
---
# <a name="pausing-and-interrupting-threads"></a>İş parçacıklarını duraklatma ve kesintiye uğratma

İş parçacıklarının etkinliklerini eşitlemenin en yaygın yolu, iş parçacıklarını engellemek ve serbest bırakmak veya nesneleri veya kod bölgelerini kilitlemektir. Bu kilitleme ve engelleme mekanizmaları hakkında daha fazla bilgi için, [Eşitleme İlkelgenel Bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md)bakın.  
  
 Ayrıca iş parçacığı kendilerini uyku koymak olabilir. İş parçacıkları engellendiğinde veya uyuduğunda, <xref:System.Threading.ThreadInterruptedException> a'yı bekleme durumlarından ayırmak için kullanabilirsiniz.  
  
## <a name="the-threadsleep-method"></a>Thread.Sleep yöntemi

 <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> Yöntemi çağırmak, geçerli iş parçacığının milisaniye sayısı veya yönteme geçtiğiniz zaman aralığı için hemen engellenmesine neden olur ve zaman diliminin geri kalanını başka bir iş parçacığına verir. Bu aralık bir kez geçince, uyku ipliği yürütmeye devam eder.  
  
 Bir iş <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> parçacığı başka bir iş parçacığı üzerinde arayamaz.  <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>her zaman geçerli iş parçacığı uyku neden statik bir yöntemdir.  
  
 Bir <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> değerle <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> arama yapmak, bir iş parçacığının uyku iş <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> parçacığı üzerindeki yöntemi çağıran başka bir iş parçacığı <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> tarafından kesintiye uğrayana veya yöntemine yapılan bir çağrıyla sonlandırılına kadar uyku moduna neden olur.  Aşağıdaki örnek, bir uyku iş parçacığı kesme her iki yöntemi göstermektedir.  
  
 [!code-csharp[Conceptual.Threading.Resuming#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Threading.Resuming/cs/Sleep1.cs#1)]
 [!code-vb[Conceptual.Threading.Resuming#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Threading.Resuming/vb/Sleep1.vb#1)]  
  
## <a name="interrupting-threads"></a>Kesme iş parçacıkları

 Engellenen iş parçacığının <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> yöntemini arayarak, iş parçacığının engelleme çağrısından kırıldığı bir <xref:System.Threading.ThreadInterruptedException>, bekleyen bir iş parçacığını kesebilirsiniz. İş parçacığı yakalamak <xref:System.Threading.ThreadInterruptedException> ve çalışmaya devam etmek için uygun ne olursa olsun yapmak gerekir. İş parçacığı özel durumu varsayılsa, çalışma zamanı özel durumu yakalar ve iş parçacığı durdurur.  
  
> [!NOTE]
> Hedef iş parçacığı çağrıldığında <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> engellenmezse, iş parçacığı engelleyene kadar kesilmez. İş parçacığı hiç engellenmezse, hiç kesintiye uğramadan tamamlanabilir.  
  
 Bekleme yönetilen bir bekleyişise, <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> her ikisi de iş parçacığıhemen uyandırır. Bekleme yönetilmeyen bir bekleyişse (örneğin, bir platform Win32 [WaitForSingleObject](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject) işlevine çağrı çağırır), <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> yönetilen koda dönene veya çağırana kadar iş parçacığının denetimini ne de denetimini alabilir. Yönetilen kodda davranış aşağıdaki gibidir:  
  
- <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>bir iş parçacığı nın içinde olabileceği herhangi bir <xref:System.Threading.ThreadInterruptedException> beklemeden uyanır ve hedef iş parçacığına atılmasına neden olur.  
  
- <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>bir iş parçacığı nın içinde olabileceği herhangi bir <xref:System.Threading.ThreadAbortException> beklemeden uyanır ve iş parçacığına atılmasına neden olur. Ayrıntılar için, [Bkz. İş Parçacığı Yok Etme](../../../docs/standard/threading/destroying-threads.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadInterruptedException>
- <xref:System.Threading.ThreadAbortException>
- [İş Parçacığı Oluşturma](../../../docs/standard/threading/index.md)
- [İş Parçacığı ve İş Parçacığı kullanma](../../../docs/standard/threading/using-threads-and-threading.md)
- [Senkronizasyon İlkellerine Genel Bakış](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
