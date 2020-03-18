---
title: Sol dış birleştirmeleri gerçekleştirin (C#'da LINQ)
description: C#'da LINQ'u kullanarak sol dış birleştirmeleri nasıl gerçekleştireceklerini öğrenin.
ms.date: 12/01/2016
ms.assetid: f542cee6-3169-4dcf-a631-3a6a79ccd473
ms.openlocfilehash: cc08a1c8670623a10d1e0bf10221d02037a8d7bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61688585"
---
# <a name="perform-left-outer-joins"></a>Sol dış birleşimler gerçekleştirme

Sol dış birleştirme, ikinci koleksiyonda ilişkili öğeler olup olmadığına bakılmaksızın, ilk koleksiyonun her öğesinin döndürüldildiği bir birleştirmedir. Bir grup birleştirme sonuçları <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> üzerinde yöntem çağırarak sol dış birleştirme gerçekleştirmek için LINQ kullanabilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki örnek, sol dış <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> birleştirme gerçekleştirmek için bir grup birleştirme sonuçlarında yöntemin nasıl kullanılacağını gösterir.

İki koleksiyonun sol dış birliğini oluşturmanın ilk adımı, grup birleştirme kullanarak bir iç birleştirme gerçekleştirmektir. (Bkz. Bu işlemin bir açıklaması için [iç birleştirmeleri](perform-inner-joins.md) gerçekleştirin.) Bu `Person` örnekte, nesnelerin listesi eşleşen `Pet` `Person` `Pet.Owner`bir nesneye dayalı nesnelerin listesine iç-joined .

İkinci adım, ilk (sol) koleksiyonun her öğesini, bu öğenin doğru koleksiyonda eşleşmesi olmasa bile sonuç kümesine eklemektir. Bu grup birleştirme <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> eşleşen öğelerin her dizi çağırarak gerçekleştirilir. Bu örnekte, <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> eşleşen `Pet` nesnelerin her dizisinde çağrılır. Yöntem, eşleşen `Pet` nesnelerin sırası herhangi `Person` bir nesne için boşsa tek bir varsayılan değer içeren `Person` bir koleksiyon döndürür ve böylece her nesnenin sonuç koleksiyonunda temsil edilmesini sağlar.

> [!NOTE]
> Bir başvuru türü için `null`varsayılan değer; bu nedenle, örnek, her `Pet` koleksiyonun her öğesine erişmeden önce null başvuru için denetler.

[!code-csharp[CsLINQProgJoining#7](~/samples/snippets/csharp/concepts/linq/how-to-perform-left-outer-joins_1.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.Enumerable.Join%2A>
- <xref:System.Linq.Enumerable.GroupJoin%2A>
- [İç birleşimler gerçekleştirme](perform-inner-joins.md)
- [Gruplanmış birleşimler gerçekleştirme](perform-grouped-joins.md)
- [Anonim türleri](../programming-guide/classes-and-structs/anonymous-types.md)
