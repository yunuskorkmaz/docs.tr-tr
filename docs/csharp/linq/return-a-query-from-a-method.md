---
title: Yöntemden sorgu döndürme
description: Sorgu nasıl döndürülecek.
ms.date: 11/30/2016
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: 1df533770f76301432b104d6f8398f1687750cce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73972520"
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a>Bir yöntemden sorgu nasıl döndürülür (C# Programlama Kılavuzu)
Bu örnek, bir yöntemden bir sorgunun iade değeri `out` olarak ve parametre olarak nasıl döndürüleceklerini gösterir.  
  
 Sorgu nesneleri birleştirilebilir, yani bir yöntemden sorgu döndürebilirsiniz. Sorguları temsil eden nesneler, ortaya çıkan koleksiyonu değil, gerektiğinde sonuçları üreten adımları depolar. Sorgu nesnelerini yöntemlerden döndürmenin avantajı, bunların daha fazla oluşturulabiliyor veya değiştirilebiliyor olmasıdır. Bu nedenle, `out` sorgu döndüren bir yöntemin herhangi bir dönüş değeri veya parametresi de bu türolmalıdır. Bir yöntem bir sorguyu somut <xref:System.Collections.Generic.List%601> veya <xref:System.Array> türe somutlaştırırsa, sorgunun kendisi yerine sorgu sonuçlarını döndürülür olarak kabul edilir. Yöntemden döndürülen bir sorgu değişkeni yine de oluşturulabilir veya değiştirilebilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, ilk yöntem bir sorguyu iade değeri olarak döndürür `out` ve ikinci yöntem bir sorguyu parametre olarak döndürür. Her iki durumda da sorgu sonuçları değil, döndürülen bir sorgu olduğunu unutmayın.  
  
 [!code-csharp[csProgGuideLINQ#80](~/samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile Tümleşik Sorgu (LINQ)](index.md)
