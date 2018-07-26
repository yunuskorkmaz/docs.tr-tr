---
title: Yöntemden sorgu döndürme
description: Sorgu döndürme yapma.
ms.date: 11/30/2016
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: 13f0839f712cb76b34c98157a30315787d300109
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404164"
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a>Nasıl yapılır: Yöntemden Sorgu Döndürme (C# Programlama Kılavuzu)
Bu örnek ve dönüş değeri olarak bir yöntemden sorgu döndürme işlemini gösterir. bir `out` parametresi.  
  
 Sorgu nesneleri yöntemden sorgu döndürme, yani birleştirilebilir. Sorguları temsil eden nesneleri, sonuçta elde edilen koleksiyon, ancak gerektiğinde, istediğiniz sonuçları vermeyebilir adımları yerine depolamayın. Sorgu nesneleri döndürme yöntemleri avantajı, bunların daha da oluşan değiştirilebilir veya emin olmanızdır. Bu nedenle herhangi bir değer döndürür veya `out` bir sorgu döndüren bir yöntem parametresi türü de olmalıdır. Bir yöntem içinde bir somut bir sorgu gerçekleştiren varsa <xref:System.Collections.Generic.List%601> veya <xref:System.Array> türü, bu olarak kabul sorgu sonuçları yerine sorguyu döndürüyor. Yöntemi tarafından döndürülen bir sorgu değişkeni yine de oluşur veya değiştirilemez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, ilk yöntem dönüş değeri olarak bir sorgu döndürür ve ikinci yöntem döndüren bir sorgu olarak bir `out` parametresi. Her iki durumda da, sorgu sonuçları, döndürülen bir sorgu olduğunu unutmayın.  
  
 [!code-csharp[csProgGuideLINQ#80](~/samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a>Ayrıca Bkz.  
 [Dil ile Tümleşik Sorgu (LINQ)](index.md)
