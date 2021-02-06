---
description: "Şu konuda daha fazla bilgi edinin: nasıl yapılır: PLıNQ 'te yürütme modunu belirtme"
title: "Nasıl yapılır: PLINQ'te Yürütme Modunu Belirtme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
ms.openlocfilehash: f897a7a2f60da1747b4cec253a98fd5608eb0f61
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641583"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a>Nasıl yapılır: PLINQ'te Yürütme Modunu Belirtme

Bu örnekte, PLıNQ 'ın varsayılan buluşsal yöntemlerini atlaması ve sorgu şeklinin ne olursa olsun bir sorgu paralel hale getirmek nasıl zorlanacağı gösterilmektedir.  
  
> [!NOTE]
> Bu örnek, kullanımı göstermeye yöneliktir ve eşdeğer sıralı LINQ to Objects sorgusundan daha hızlı çalışmayabilir. Hızlı yedekleme hakkında daha fazla bilgi için bkz. [PLıNQ 'Te hızlı hızlandırı anlama](understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Örnek  

 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 PLıNQ, paralelleştirme için fırsatlardan yararlanmak üzere tasarlanmıştır. Ancak, tüm sorgular paralel yürütmeden faydalanır. Örneğin, bir sorgu çok az iş yapan tek bir kullanıcı temsilcisi içerdiğinde, sorgu genellikle sırayla daha hızlı çalışır. Paralel yürütme daha hızlıdır, çünkü paralelleştirme yürütmesinin etkinleştirilmesindeki ek yük, elde edilen hızlı hale getirme özelliğinden daha pahalıdır. Bu nedenle, PLıNQ her sorguyu otomatik olarak paralel hale getirmek. Önce sorgunun şeklini ve onu oluşturan çeşitli işleçleri inceler. Bu analize dayalı olarak, varsayılan yürütme modundaki PLıNQ sorgunun bir kısmını veya tümünü ardışık olarak yürütmeye karar verebilir. Ancak bazı durumlarda, sorgunuz hakkında PLıNQ ' den daha fazla bilgi sahibi olabilirsiniz. Örneğin, bir temsilcinin pahalı olduğunu ve sorgunun paralelleştirmeyi kesinlikle yararlı olacağını bilirsiniz. Bu gibi durumlarda <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> yöntemini kullanabilir ve <xref:System.Linq.ParallelExecutionMode.ForceParallelism> PLINQ 'ın sorguyu her zaman paralel olarak çalıştırmasını istemek için değeri belirtebilirsiniz.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  

 Bu kodu kesip [PLINQ veri örneğine](plinq-data-sample.md) yapıştırın ve öğesinden yöntemi çağırın `Main` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>
- [Paralel LINQ (PLINQ)](introduction-to-plinq.md)
