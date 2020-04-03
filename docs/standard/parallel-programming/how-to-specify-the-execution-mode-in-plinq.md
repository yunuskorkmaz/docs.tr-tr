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
ms.openlocfilehash: f035dbcd5091d81a3cce3b9e9e683d836fe84bb7
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635819"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a>Nasıl yapılır: PLINQ'te Yürütme Modunu Belirtme

Bu örnek, PLINQ'yi varsayılan sezgisel'ini atlayarak nasıl zorlayacağını ve sorgunun şekline bakılmaksızın sorguyu paralelleştirmeyi gösterir.  
  
> [!NOTE]
> Bu örnek, kullanımı göstermek için tasarlanmıştır ve Nesneler sorgusuna eşdeğer ardışık LINQ'dan daha hızlı çalışmayabilir. Hız hakkında daha fazla bilgi için [PLINQ'da Hızları Anlama'ya](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)bakın.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 PLINQ, paralelleştirme fırsatlarından yararlanmak için tasarlanmıştır. Ancak, tüm sorgular paralel yürütme yarar. Örneğin, bir sorgu çok az iş yapan tek bir kullanıcı temsilcisi içeriyorsa, sorgu genellikle sırayla daha hızlı çalışır. Paralelyürütmeyi etkinleştirmede yer alan ek yükü elde edilen hızdan daha pahalı olduğundan, sıralı yürütme daha hızlıdır. Bu nedenle, PLINQ otomatik olarak her sorgu paraleldeğildir. Önce sorgunun şeklini ve onu oluşturan çeşitli işleçleri inceler. Bu çözümlemedayanarak, varsayılan yürütme modundaPLINQ, sorgunun bir kısmını veya tamamını sırayla yürütmeye karar verebilir. Ancak, bazı durumlarda, PLINQ onun analizinden belirlemek mümkün daha sorgu hakkında daha fazla bilgi edinebilirsiniz. Örneğin, bir temsilcinin pahalı olduğunu ve sorgunun kesinlikle paralelleştirmeden yararlanacağını biliyor olabilirsiniz. Bu gibi durumlarda, <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> yöntemi kullanabilir ve <xref:System.Linq.ParallelExecutionMode.ForceParallelism> PLINQ'a sorguyu her zaman paralel olarak çalıştırmasını söylemek için değeri belirtebilirsiniz.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu kodu [PLINQ Veri Örneği'ne](../../../docs/standard/parallel-programming/plinq-data-sample.md) kesip yapıştırın ve yöntemi .'den `Main`çağırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>
- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
