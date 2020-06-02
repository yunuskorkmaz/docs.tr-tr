---
title: "Nasıl yapılır: PLINQ'te Yürütme Modunu Belirtme"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
ms.openlocfilehash: 39ccde003b60ac9cbcff7ab824103a9cf37cc453
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288101"
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
