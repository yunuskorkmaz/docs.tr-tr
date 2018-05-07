---
title: Bir sorgu döndürme
description: Bir sorgu iade etme.
ms.date: 11/30/2016
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: 6a1d581c46c7b0b2062859fd60701dd25ea54eea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a>Nasıl yapılır: Yöntemden Sorgu Döndürme (C# Programlama Kılavuzu)
Bu örnek bir sorgu ve dönüş değeri olarak döndürme gösterilmektedir bir `out` parametresi.  
  
 Sorgu nesneleri birleştirilebilir bir yöntemden sorgu döndürebilir anlamına gelir. Sorguları temsil eden nesneler, sonuçta elde edilen koleksiyonu, ancak gerektiğinde sonuçlar yerine adımlarını depolamayın. Yöntemleri sorgu nesneleri döndürme avantajı, bunların daha oluşan değiştirilebilir veya olduğunu olmasıdır. Bu nedenle herhangi bir değeri döndürme veya `out` bir sorgu döndüren bir yöntem parametresinin türü de olması gerekir. Bir yöntem somut bir sorgu gerçeğe varsa <xref:System.Collections.Generic.List%601> veya <xref:System.Array> türü, onu olarak kabul sorgu yerine sorgu sonuçları döndürüyor. Bir yöntemin döndürdüğü bir sorgu değişkeni hala oluşur veya değiştirilemez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, ilk yöntem sorgu dönüş değeri olarak döndürür ve bir sorgu olarak ikinci yöntem bir `out` parametresi. Her iki durumda da, sorgu sonuçları döndüren bir sorgu olduğuna dikkat edin.  
  
 [!code-csharp[csProgGuideLINQ#80](../../../samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ Sorgu ifadeleri](index.md)
