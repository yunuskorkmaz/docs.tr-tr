---
title: (C# üzerinde LINQ) sol dış birleştirmeler gerçekleştirme
description: C# içinde LINQ kullanarak sol dış birleştirmeler gerçekleştirme konusunda bilgi edinin.
ms.date: 12/1/2016
ms.assetid: f542cee6-3169-4dcf-a631-3a6a79ccd473
ms.openlocfilehash: 329fe9e17640931c5eb39b33b791a7a77a6f7b89
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506602"
---
# <a name="perform-left-outer-joins"></a>Sol dış birleştirmeler gerçekleştirme

Sol dış birleşim bir birleşim olduğunu, hangi ilk koleksiyonun her öğesine, bunu herhangi bir bağlantılı öğe ikinci koleksiyonda olup bağımsız olarak döndürülür. LINQ çağırarak bir sol dış birleşim gerçekleştirmek için kullanabileceğiniz <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> Grup birleştirme sonuçlarının yöntemi.

## <a name="example"></a>Örnek

Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> bir grup birleşimin sol dış birleşim sonuçlara göre yöntemi.

Bir sol dış birleşim iki koleksiyon oluşturmayı ilk adımı, bir grup birleşim kullanarak bir iç birleştirme gerçekleştirmektir. (Bkz [iç birleştirmeler gerçekleştirme](perform-inner-joins.md) bu işlemin açıklaması.) Bu örnekte, listesini `Person` nesneleri, iç katılmış listesine `Pet` nesneleri temel alan bir `Person` eşleşen nesne `Pet.Owner`.

İkinci adım sonuç o öğenin sağ koleksiyondaki herhangi bir eşleşme olsa bile kümesinde (soldaki) ilk koleksiyonun her öğesine eklemektir. Bu çağrılarak gerçekleştirilir <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> group JOIN öğelerden eşleşen her dizisi üzerinde. Bu örnekte, <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> eşleşen her sırası adlı `Pet` nesneleri. Yöntemi, tek bir varsayılan değer içeren bir koleksiyon döndürür eşleşen dizisi `Pet` nesneleri için boş `Person` nesne, böylece, her sağlama `Person` nesne sonucu koleksiyonda temsil edilir.

> [!NOTE]
> Bir başvuru türü için varsayılan değerdir `null`; bu nedenle, her birinin her öğe erişmeden önce bir null başvuru için örnek denetler `Pet` koleksiyonu.

[!code-csharp[CsLINQProgJoining#7](~/samples/snippets/csharp/concepts/linq/how-to-perform-left-outer-joins_1.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.Enumerable.Join%2A>  
- <xref:System.Linq.Enumerable.GroupJoin%2A>  
- [İç birleşimler gerçekleştirme](perform-inner-joins.md)  
- [Gruplanmış birleşimler gerçekleştirme](perform-grouped-joins.md)  
- [Anonim türler](../programming-guide/classes-and-structs/anonymous-types.md)  