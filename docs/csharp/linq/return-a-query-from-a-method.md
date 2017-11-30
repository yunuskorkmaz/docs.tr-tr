---
title: "Bir sorgu döndürme"
description: Bir sorgu iade etme.
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: c1b69e3f5f0cd2c50ae80d2454e6b7f13dc30344
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a>Nasıl yapılır: Yöntemden Sorgu Döndürme (C# Programlama Kılavuzu)
Bu örnek bir sorgu ve dönüş değeri olarak döndürme gösterilmektedir bir `out` parametresi.  
  
 Sorgu nesneleri birleştirilebilir bir yöntemden sorgu döndürebilir anlamına gelir. Sorguları temsil eden nesneler, sonuçta elde edilen koleksiyonu, ancak gerektiğinde sonuçlar yerine adımlarını depolamayın. Yöntemleri sorgu nesneleri döndürme avantajı, bunların daha oluşan değiştirilebilir veya olduğunu olmasıdır. Bu nedenle herhangi bir değeri döndürme veya `out` bir sorgu döndüren bir yöntem parametresinin türü de olması gerekir. Bir yöntem somut bir sorgu gerçeğe varsa <xref:System.Collections.Generic.List%601> veya <xref:System.Array> türü, onu olarak kabul sorgu yerine sorgu sonuçları döndürüyor. Bir yöntemin döndürdüğü bir sorgu değişkeni hala oluşur veya değiştirilemez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, ilk yöntem sorgu dönüş değeri olarak döndürür ve bir sorgu olarak ikinci yöntem bir `out` parametresi. Her iki durumda da, sorgu sonuçları döndüren bir sorgu olduğuna dikkat edin.  
  
 [!code-csharp[csProgGuideLINQ#80](../../../samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ Sorgu ifadeleri](index.md)
