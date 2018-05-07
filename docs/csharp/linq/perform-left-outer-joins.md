---
title: Sol dış birleştirmeler gerçekleştirme
description: Sol dış birleştirmeler gerçekleştirme.
ms.date: 12/1/2016
ms.assetid: f542cee6-3169-4dcf-a631-3a6a79ccd473
ms.openlocfilehash: aacab1ac6f4ab2c10b393cf0b2c578a13d9b9306
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="perform-left-outer-joins"></a>Sol dış birleştirmeler gerçekleştirme
Sol dış birleşim bir birleşim değil de, ilk koleksiyonun her öğesine, bunu herhangi bir ilişkili öğe ikinci koleksiyonda olup bağımsız olarak döndürülür. LINQ çağırarak bir sol dış birleşim gerçekleştirmek için kullanabileceğiniz <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> group JOIN sonuçlarını yöntemi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl kullanılacağı ortaya <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> bir sol dış birleşim gerçekleştirmek için bir grup birleştirme sonuçlarını yöntemi.  
  
 Sol dış birleşim iki koleksiyonların oluşturan ilk adımı, bir grup birleşim kullanarak bir iç birleştirme gerçekleştirmektir. (Bkz [iç birleştirmeler gerçekleştirme](perform-inner-joins.md) bu işlemin bir açıklama için.) Bu örnekte, listesini `Person` nesneleri iç katılmış listesine `Pet` nesneleri temel alarak bir `Person` eşleşen nesne `Pet.Owner`.  
  
 İkinci adım sonuç o öğeye sağ koleksiyonunda herhangi bir eşleşme sahip olsa bile kümesinde ilk (soldaki) koleksiyonun her öğesine eklemektir. Bu çağırarak gerçekleştirilir <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> group JOIN öğelerinden eşleşen her dizisi üzerinde. Bu örnekte, <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> eşleşen her dizisi adlı `Pet` nesneleri. Yöntemi, tek bir varsayılan değer içeren bir koleksiyon döndürür eşleşen sırası `Pet` nesneleri için boş `Person` nesnesi, böylece, her sağlar `Person` nesne sonucu koleksiyonunda temsil edilir.  
  
> [!NOTE]
>  Bir başvuru türü için varsayılan değer `null`; bu nedenle, her birinin her öğe erişmeden önce bir null başvuru için örnek denetler `Pet` koleksiyonu.  
  
 [!code-csharp[CsLINQProgJoining#7](../../../samples/snippets/csharp/concepts/linq/how-to-perform-left-outer-joins_1.cs)]  
 
## <a name="see-also"></a>Ayrıca bkz.  
 <xref:System.Linq.Enumerable.Join%2A>  
 <xref:System.Linq.Enumerable.GroupJoin%2A>  
 [İç birleşimler gerçekleştirme](perform-inner-joins.md)  
 [Gruplanmış birleşimler gerçekleştirme](perform-grouped-joins.md)  
 [Anonim türler](../programming-guide/classes-and-structs/anonymous-types.md)  
 
