---
title: Bellekte sorgunun sonuçlarını depolama
description: Sonuçları deposunu yapma.
ms.date: 11/30/2016
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: c125d134d7c1db98363844c12fc8abd3faa9c868
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33279639"
---
# <a name="store-the-results-of-a-query-in-memory"></a>Bellekte sorgunun sonuçlarını depolama

Bir sorguyu temel alabilir ve verileri düzenlemek hakkında yönergeler kümesidir. İstenen sonuç sonraki her öğe olarak sorguları gevşek, yürütülür. Kullandığınızda `foreach` sonuçları yinelemek için öğeler erişilen olarak döndürülür. Bir sorguyu değerlendirmek ve sonuçlarını çalıştırmadan depolamak için bir `foreach` döngü, yalnızca aşağıdaki yöntemlerden birini sorgu değişkeni üzerine çağırırsınız:  
  
-   <xref:System.Linq.Enumerable.ToList%2A>  
  
-   <xref:System.Linq.Enumerable.ToArray%2A>  
  
-   <xref:System.Linq.Enumerable.ToDictionary%2A>  
  
-   <xref:System.Linq.Enumerable.ToLookup%2A>  
  
 Sorgu sonuçları depoladığınızda, döndürülen koleksiyon nesnesi için yeni bir değişken aşağıdaki örnekte gösterildiği gibi atamanızı öneririz:  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideLINQ#25](../../../samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]  
  

## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ Sorgu ifadeleri](index.md)
