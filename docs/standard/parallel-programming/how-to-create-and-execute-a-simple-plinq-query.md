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
ms.openlocfilehash: 544ea0f89dfa518c2ef18bffe2609d72e6fdee70
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43891226"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a>Nasıl yapılır: Basit bir PLINQ Sorgusu Oluşturma ve Yürütme
Aşağıdaki örnek, kullanarak basit bir paralel LINQ Sorgu oluşturma işlemi gösterilmektedir <xref:System.Linq.ParallelEnumerable.AsParallel%2A> kaynak sırası ve kullanarak sorgu yürütülürken genişletme yöntemini <xref:System.Linq.ParallelEnumerable.ForAll%2A> yöntemi.  
  
> [!NOTE]
>  Bu belgede lambda ifadeleri PLINQ'te temsilciler tanımlamak için kullanılır. C# veya Visual Basic'te lambda ifadelerine aşina değilseniz bkz [PLINQ ve TPL'deki Lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 Bu örnek, oluşturmak ve sonucu bir dizi sırası önemli değildir, herhangi bir paralel LINQ Sorgu yürütme için temel düzeni gösterir; Sıralanmamış sorgular genellikle sıralı sorgular hızlıdır. Sorgu, birden çok iş parçacığında zaman uyumsuz olarak yürütülür görevlere kaynak bölümler. İçinde her görev tamamlandığında sırası, yalnızca iş öğeleri bölümünde işlemek için aynı zamanda işletim sistemi her iş parçacığı nasıl zamanlamaları gibi dış etkenlerle ilişkilerini bağlıdır. Bu örnek, kullanımını göstermek için tasarlanmıştır ve nesneleri sorgu için eşdeğer sıralı LINQ daha hızlı çalışmayabilir. Hızlandırmayı hakkında daha fazla bilgi için bkz: [plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md). Sorguda öğelerin sıralamasını koruması hakkında daha fazla bilgi için bkz [nasıl yapılır: PLINQ sorgusunda denetimi sıralama](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
