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
ms.openlocfilehash: 86011cff71fabed5e47e085f91b1759238638c9a
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588498"
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a>Nasıl yapılır: PLINQ Sorgusunda Sıralama Denetimi
Bu örnekler, uzantı yöntemini kullanarak PLINQ sorgusunda sıralamanın nasıl denetlenebildiğini <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> gösterir.  
  
> [!WARNING]
> Bu örnekler öncelikle kullanımı göstermek için tasarlanmıştır ve Nesneler sorgularına eşdeğer ardışık LINQ'dan daha hızlı çalışabilir veya çalışmayabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, kaynak dizinin sırasını korur. Bu bazen gereklidir; örneğin, bazı sorgu işleçleri doğru sonuçlar üretmek için sıralı bir kaynak sıragerektirir.  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, kaynak sırası büyük olasılıkla sıralanmış olması beklenen bazı sorgu işleçleri gösterir. Bu işleçler sıralanmamış diziler üzerinde çalışır, ancak beklenmeyen sonuçlar üretebilir.  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 Bu yöntemi çalıştırmak için [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) projesinde PLINQDataSample sınıfına yapıştırın ve F5 tuşuna basın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sorgunun ilk bölümü için sıralamayı nasıl koruyacağını, ardından birleştirilmiş tümcenin performansını artırmak için sıralamayı nasıl kaldıracağını ve ardından son sonuç dizisine sıralamayı yeniden uygulayacağını gösterir.  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 Bu yöntemi çalıştırmak için [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) projesinde PLINQDataSample sınıfına yapıştırın ve F5 tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.ParallelEnumerable>
- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
