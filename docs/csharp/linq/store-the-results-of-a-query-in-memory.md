---
title: "Bellekte sorgunun sonuçlarını depolama"
description: "Sonuçları deposunu yapma."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: 86a9c2d464eac83cabb5faa68987ad580fc31248
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2017
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
