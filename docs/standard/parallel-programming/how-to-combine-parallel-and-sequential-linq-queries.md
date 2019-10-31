---
title: 'Nasıl yapılır: Paralel ve Sıralı LINQ Sorgularını Birleştirme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel queries, combine parallel and sequential
ms.assetid: 1167cfe6-c8aa-4096-94ba-c66c3a4edf4c
ms.openlocfilehash: 4c04afb23a168a9cff60962bd5a75a65e3ebca4d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134191"
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a>Nasıl yapılır: Paralel ve Sıralı LINQ Sorgularını Birleştirme
Bu örnek, PLıNQ 'ın sorgudaki sonraki işleçleri sırayla işlemesini söylemek için <xref:System.Linq.ParallelEnumerable.AsSequential%2A> yönteminin nasıl kullanılacağını gösterir. Sıralı işleme genellikle paralel olandan daha yavaş olsa da, bazen doğru sonuçların üretilmesi gerekir.  
  
> [!WARNING]
> Bu örnek, kullanımı göstermeye yöneliktir ve eşdeğer sıralı LINQ to Objects sorgusundan daha hızlı çalışmayabilir. Hızlı yedekleme hakkında daha fazla bilgi için bkz. [PLıNQ 'Te hızlı hızlandırı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, sorgunun önceki bir yan tümcesinde oluşturulan sıralamayı korumak için <xref:System.Linq.ParallelEnumerable.AsSequential%2A> gerekli olduğu bir senaryo gösterilmektedir.  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu kodu derlemek ve çalıştırmak için, [PLINQ veri örneği](../../../docs/standard/parallel-programming/plinq-data-sample.md) projesine yapıştırın, `Main`yöntemi çağırmak için bir satır ekleyin ve F5 tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
