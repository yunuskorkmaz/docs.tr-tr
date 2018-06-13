---
title: 'Nasıl yapılır: Basit bir PLINQ Sorgusu Oluşturma ve Yürütme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create
ms.assetid: 983b4213-bddd-4a44-9262-cbe59186df4c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e5bd27dda4bacc50672cca2db38a6eda746d79b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580383"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a>Nasıl yapılır: Basit bir PLINQ Sorgusu Oluşturma ve Yürütme
Aşağıdaki örnek kullanarak basit bir paralel LINQ sorgu oluşturmak nasıl gösterir <xref:System.Linq.ParallelEnumerable.AsParallel%2A> genişletme yöntemi kaynak sıradaki ve kullanarak sorgu yürütülürken <xref:System.Linq.ParallelEnumerable.ForAll%2A> yöntemi.  
  
> [!NOTE]
>  Bu belge lambda ifadeleri temsilciler PLINQ'te tanımlamak için kullanır. C# veya Visual Basic'deki lambda ifadeleri alışık değilseniz bkz [PLINQ ve TPL'deki Lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 Örnek oluşturma ve herhangi bir paralel LINQ Sorgu sonuç dizi sıralaması önemli olmadığında yürütme temel düzeni gösterir; Sıralanmamış sorgular genellikle sıralı sorguları hızlıdır. Sorgu zaman uyumsuz olarak birden çok iş parçacığı üzerinde yürütülen görevler içine kaynak bölümler. İçinde her görev tamamlandığında sırası yalnızca bölüm öğeleri işlemek için ilgili iş miktarı, aynı zamanda işletim sistemi her iş parçacığı nasıl zamanlar gibi dış faktörlere bağlıdır. Bu örnek kullanım göstermeye yöneliktir ve eşdeğer sıralı LINQ daha hızlı nesneleri sorguya çalışmayabilir. Speedup hakkında daha fazla bilgi için bkz: [Plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md). Sorguda öğeleri sıralama korumak hakkında daha fazla bilgi için bkz: [nasıl yapılır: Denetim sıralama PLINQ sorgusunda](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
