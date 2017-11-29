---
title: "Nasıl yapılır: Paralel ve Sıralı LINQ Sorgularını Birleştirme"
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
helpviewer_keywords: parallel queries, combine parallel and sequential
ms.assetid: 1167cfe6-c8aa-4096-94ba-c66c3a4edf4c
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4da91ff535059b181baa637164a854cd75d06334
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a>Nasıl yapılır: Paralel ve Sıralı LINQ Sorgularını Birleştirme
Bu örnek nasıl kullanılacağını gösterir <xref:System.Linq.ParallelEnumerable.AsSequential%2A> PLINQ sorgusunda tüm sonraki işleçleri sıralı olarak işlediğinden istemek üzere yöntemi. Bazen sıralı işleme genellikle paralel yavaş olsa da, doğru sonuçlar üretmek için gerekli.  
  
> [!WARNING]
>  Bu örnek kullanım göstermeye yöneliktir ve eşdeğer sıralı LINQ daha hızlı nesneleri sorguya çalışmayabilir. Speedup hakkında daha fazla bilgi için bkz: [Plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir senaryo gösterir <xref:System.Linq.ParallelEnumerable.AsSequential%2A> , yani için gereklidir. önceki bir sorgu yan tümcesinde kuruldu sıralama korumak.  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Derlemek ve bu kodu çalıştırmak için yapıştırın [PLINQ veri örneği](../../../docs/standard/parallel-programming/plinq-data-sample.md) yöntemini çağırmak için bir satır ekleyin, proje `Main`, F5 tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
