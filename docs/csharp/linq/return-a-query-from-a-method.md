---
title: Yöntemden sorgu döndürme
description: Sorgu döndürme.
ms.date: 11/30/2016
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: 646e771d637aa242231e3fe216d4a856bb156649
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203338"
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a>Bir yöntemden sorgu döndürme (C# Programlama Kılavuzu)

Bu örnek, bir yöntemden dönüş değeri olarak ve bir parametre olarak bir sorgunun nasıl döndürülyapılacağını gösterir `out` .  
  
 Sorgu nesneleri birleştirilebilir, bu da bir yöntemden sorgu döndürebilmeniz anlamına gelir. Sorguları temsil eden nesneler, sonuçta elde edilen koleksiyonu depolamaz, ancak gerektiğinde sonuçları oluşturmak için gerekli adımları uygulayın. Yöntemlerin sorgu nesnelerini döndürmesinin avantajı, daha fazla oluşturulabilir veya değiştirilebilir. Bu nedenle, `out` bir sorgu döndüren bir yöntemin dönüş değeri veya parametresi de bu türde olmalıdır. Bir yöntem bir sorguyu somut <xref:System.Collections.Generic.List%601> veya <xref:System.Array> türe alıyorsa, sorgunun kendisi yerine sorgu sonuçlarının döndürülmediği kabul edilir. Bir yöntemden döndürülen bir sorgu değişkeni hala oluşturulabilir veya değiştirilebilir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnekte, ilk yöntem bir sorgu dönüş değeri olarak döndürür ve ikinci yöntem parametre olarak bir sorgu döndürür `out` . Her iki durumda da, sorgu sonuçlarının değil, döndürülen bir sorgu olduğunu unutmayın.  
  
 [!code-csharp[csProgGuideLINQ#80](~/samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile Tümleşik Sorgu (LINQ)](index.md)
