---
title: "Nasıl yapılır: PLINQ'te Birleştirme Seçeneklerini Belirtme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use merge options
ms.assetid: 0f33b527-e91a-4550-a39a-e63e396fd831
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 59ffff3019f10874bd2df977b80d46e903d13613
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-specify-merge-options-in-plinq"></a>Nasıl yapılır: PLINQ'te Birleştirme Seçeneklerini Belirtme
Bu örnekte, tüm sonraki işleçleri PLINQ sorgusunda uygulanacak birleştirme seçeneklerini belirtme gösterilmektedir. Birleştirme seçeneklerini açıkça ayarlamak gerekmez, ancak bunu yaparsanız, bu nedenle performansını artırabilir. Birleştirme seçenekleri hakkında daha fazla bilgi için bkz: [plınq'te birleştirme seçeneklerini](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).  
  
> [!WARNING]
>  Bu örnek kullanım göstermeye yöneliktir ve eşdeğer sıralı LINQ daha hızlı nesneleri sorguya çalışmayabilir. Speedup hakkında daha fazla bilgi için bkz: [Plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sırasız bir kaynak ve her öğeye pahalı işlevi uygular temel bir senaryoda birleştirme seçeneklerini davranışını gösterir.  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 Durumlarda nerede <xref:System.Linq.ParallelMergeOptions.AutoBuffered> seçeneği doğurur istenmeyen bir gecikme süresi ilk öğe verdiğini önce deneyin <xref:System.Linq.ParallelMergeOptions.NotBuffered> sonuç öğeleri daha hızlı ve daha sorunsuz bir şekilde elde etmek üzere seçeneği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Linq.ParallelMergeOptions>  
 [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
