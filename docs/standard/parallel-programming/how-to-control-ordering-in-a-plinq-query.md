---
title: 'Nasıl yapılır: PLINQ Sorgusunda Sıralama Denetimi'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to control ordering
ms.assetid: c67eccc7-004d-4b2f-987e-919cbbd62ef7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aaa08106126212345bb594cdeabe6e7281cd7b5e
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45668894"
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a>Nasıl yapılır: PLINQ Sorgusunda Sıralama Denetimi
Bu örnekler kullanarak bir PLINQ sorgusunda sıralama denetimi nasıl <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> genişletme yöntemi.  
  
> [!WARNING]
>  Bu örnek kullanımını göstermek için tasarlanmıştır ve olabilir veya eşdeğer sıralı LINQ hızlıdır Plınq sorgularının çalışmayabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, kaynak dizi sıralamasını korur. Bu bazen gereklidir. Örneğin bazı sorgu işleçleri doğru sonuçlar için bir sıralanmış kaynak dizisi gerektirir.  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterildiği bazı sorgu işleçleri olan kaynak dizisi, büyük olasılıkla sıralanabilmesi beklenir. Bu işleçler, sırasız dizileri üzerinde çalışır, ancak beklenmeyen sonuçlara neden.  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 Bu yöntem çalıştırılacak PLINQDataSample sınıfında yapıştırın [PLINQ veri örneği](../../../docs/standard/parallel-programming/plinq-data-sample.md) proje ve F5 tuşuna basın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir sorgu için ilk bölümünü sıralamasını korumak sonra join tümcesinin performansını artırmak için sıralama kaldırma ve sıralama için Sonuç dizisi'ı yeniden gösterilmektedir.  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 Bu yöntem çalıştırılacak PLINQDataSample sınıfında yapıştırın [PLINQ veri örneği](../../../docs/standard/parallel-programming/plinq-data-sample.md) proje ve F5 tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.ParallelEnumerable>  
- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
