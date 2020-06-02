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
ms.openlocfilehash: 84667fa1fbe2966c580d9c6d32e52ed686af7bb3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288127"
---
# <a name="how-to-specify-merge-options-in-plinq"></a>Nasıl yapılır: PLINQ'te Birleştirme Seçeneklerini Belirtme
Bu örnekte, bir PLıNQ sorgusunda sonraki tüm işleçlere uygulanacak birleştirme seçeneklerinin nasıl ayarlanacağı gösterilmektedir. Birleştirme seçeneklerini açıkça ayarlamanız gerekmez, ancak bunu yapmak performansı iyileştirebilir. Birleştirme seçenekleri hakkında daha fazla bilgi için bkz. [PLıNQ Içindeki birleştirme seçenekleri](merge-options-in-plinq.md).  
  
> [!WARNING]
> Bu örnek, kullanımı göstermeye yöneliktir ve eşdeğer sıralı LINQ to Objects sorgusundan daha hızlı çalışmayabilir. Hızlı yedekleme hakkında daha fazla bilgi için bkz. [PLıNQ 'Te hızlı hızlandırı anlama](understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sıralanmamış bir kaynağı olan temel bir senaryoda birleştirme seçeneklerinin davranışını gösterir ve her öğeye pahalı bir işlev uygular.  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 <xref:System.Linq.ParallelMergeOptions.AutoBuffered>Seçeneğin ilk öğeden önce istenmeyen bir gecikme olduğu durumlarda, <xref:System.Linq.ParallelMergeOptions.NotBuffered> sonuç öğelerini daha hızlı ve daha sorunsuz bir şekilde sunun seçeneğini deneyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.ParallelMergeOptions>
- [Paralel LINQ (PLINQ)](introduction-to-plinq.md)
