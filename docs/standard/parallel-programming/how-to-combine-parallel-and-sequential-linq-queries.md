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
ms.openlocfilehash: 2bdf074bc2977dc501e0726a52e825c89828565f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289544"
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a>Nasıl yapılır: Paralel ve Sıralı LINQ Sorgularını Birleştirme

Bu örnek, <xref:System.Linq.ParallelEnumerable.AsSequential%2A> PLıNQ 'ın sorgudaki sonraki işleçleri sırayla işlemesini sağlamak için yönteminin nasıl kullanılacağını gösterir. Sıralı işleme genellikle paralel olandan daha yavaş olsa da, bazen doğru sonuçlar üretmeniz gerekir.  
  
> [!NOTE]
> Bu örnek, kullanımı göstermeye yöneliktir ve eşdeğer sıralı LINQ to Objects sorgusundan daha hızlı çalışmayabilir. Hızlı yedekleme hakkında daha fazla bilgi için bkz. [PLıNQ 'Te hızlı hızlandırı anlama](understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Linq.ParallelEnumerable.AsSequential%2A> sorgunun önceki bir yan tümcesinde oluşturulan sıralamayı korumak için gereken bir senaryoyu gösterir.  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu kodu derlemek ve çalıştırmak için, [PLINQ veri örneği](plinq-data-sample.md) projesine yapıştırın, öğesinden yöntemi çağırmak için bir satır ekleyin `Main` ve **F5**tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel LINQ (PLINQ)](introduction-to-plinq.md)
