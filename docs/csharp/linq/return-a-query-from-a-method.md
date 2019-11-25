---
title: Yöntemden sorgu döndürme
description: Sorgu döndürme.
ms.date: 11/30/2016
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: 1df533770f76301432b104d6f8398f1687750cce
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73972520"
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a>Yöntemden bir sorgu döndürme (C# Programlama Kılavuzu)
Bu örnek, bir yöntemden dönüş değeri olarak ve `out` parametresi olarak bir sorgunun nasıl döndürülyapılacağını gösterir.  
  
 Sorgu nesneleri birleştirilebilir, bu da bir yöntemden sorgu döndürebilmeniz anlamına gelir. Sorguları temsil eden nesneler, sonuçta elde edilen koleksiyonu depolamaz, ancak gerektiğinde sonuçları oluşturmak için gerekli adımları uygulayın. Yöntemlerin sorgu nesnelerini döndürmesinin avantajı, daha fazla oluşturulabilir veya değiştirilebilir. Bu nedenle, bir sorgu döndüren bir yöntemin dönüş değeri veya `out` parametresi de aynı türde olmalıdır. Bir yöntem bir sorguyu somut bir <xref:System.Collections.Generic.List%601> veya <xref:System.Array> türüne alıyorsa, sorgunun kendisi yerine sorgu sonuçlarının döndürülmesi kabul edilir. Bir yöntemden döndürülen bir sorgu değişkeni hala oluşturulabilir veya değiştirilebilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, ilk yöntem bir sorgu dönüş değeri olarak döndürür ve ikinci yöntem `out` parametresi olarak bir sorgu döndürür. Her iki durumda da, sorgu sonuçlarının değil, döndürülen bir sorgu olduğunu unutmayın.  
  
 [!code-csharp[csProgGuideLINQ#80](~/samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile Tümleşik Sorgu (LINQ)](index.md)
