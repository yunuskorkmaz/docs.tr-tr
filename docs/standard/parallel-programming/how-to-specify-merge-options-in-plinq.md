---
title: "Nasıl yapılır: PLINQ'te Birleştirme Seçeneklerini Belirtme"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use merge options
ms.assetid: 0f33b527-e91a-4550-a39a-e63e396fd831
ms.openlocfilehash: 40abe2f101f6fa23d804ef30e27d642a36908196
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139274"
---
# <a name="how-to-specify-merge-options-in-plinq"></a>Nasıl yapılır: PLINQ'te Birleştirme Seçeneklerini Belirtme
Bu örnek, plinq sorgusunda sonraki tüm işleçler için geçerli olacak birleştirme seçeneklerini nasıl belirteceğini gösterir. Birleştirme seçeneklerini açıkça ayarlamanız gerekmez, ancak bunu yapmak performansı artırabilir. Birleştirme seçenekleri hakkında daha fazla bilgi için [PLINQ'da Birleştirme Seçenekleri'ne](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)bakın.  
  
> [!WARNING]
> Bu örnek, kullanımı göstermek için tasarlanmıştır ve Nesneler sorgusuna eşdeğer ardışık LINQ'dan daha hızlı çalışmayabilir. Hız hakkında daha fazla bilgi için [PLINQ'da Hızları Anlama'ya](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)bakın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sıralanmamış bir kaynağa sahip ve her öğeiçin pahalı bir işlev uygulayan temel bir senaryoda birleştirme seçeneklerinin davranışını gösterir.  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 Seçeneğin <xref:System.Linq.ParallelMergeOptions.AutoBuffered> ilk öğe verilmeden önce istenmeyen bir gecikmeye neden olduğu durumlarda, sonuç öğelerini <xref:System.Linq.ParallelMergeOptions.NotBuffered> daha hızlı ve daha sorunsuz bir şekilde verim verme seçeneğini deneyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.ParallelMergeOptions>
- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
