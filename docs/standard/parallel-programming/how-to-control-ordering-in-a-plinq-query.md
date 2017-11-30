---
title: "Nasıl yapılır: PLINQ Sorgusunda Sıralama Denetimi"
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
helpviewer_keywords: PLINQ queries, how to control ordering
ms.assetid: c67eccc7-004d-4b2f-987e-919cbbd62ef7
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b9e29aa825a68154e32a34a23ca170258092b88a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a>Nasıl yapılır: PLINQ Sorgusunda Sıralama Denetimi
Bu örnekler kullanarak bir PLINQ sorgusunda sıralama denetleme <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> genişletme yöntemi.  
  
> [!WARNING]
>  Bu örnekler kullanımını göstermek için tasarlanmıştır ve olabilir veya eşdeğer sıralı LINQ daha hızlı nesneleri sorguları çalışmayabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, kaynak dizi sıralaması korur. Bu bazen gereklidir; Örneğin bazı sorgu işleçleri doğru sonuçlar üretmek için sıralı kaynak dizisi gerektirir.  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, bazı olan kaynak sırası, büyük olasılıkla sıralanmalıdır beklenir işleçleri sorgu görülmektedir. Bu işleçlere sırasız sıraları üzerinde çalışır, ancak beklenmeyen sonuçlara neden.  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 Bu yöntem çalıştırmak için PLINQDataSample sınıfında yapıştırın [PLINQ veri örneği](../../../docs/standard/parallel-programming/plinq-data-sample.md) proje ve F5 tuşuna basın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir sorgu ilk bölümü için sıralama korumak sonra bir JOIN yan tümcesi performansını artırmak için sıralama kaldırın ve son sonucu dizisi sıralama yeniden gösterilmektedir.  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 Bu yöntem çalıştırmak için PLINQDataSample sınıfında yapıştırın [PLINQ veri örneği](../../../docs/standard/parallel-programming/plinq-data-sample.md) proje ve F5 tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Linq.ParallelEnumerable>  
 [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
