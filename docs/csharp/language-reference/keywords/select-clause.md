---
title: select tümcesi - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
ms.openlocfilehash: 3ba52fccc0521df1a0bb5b6177575dc5d2152248
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633834"
---
# <a name="select-clause-c-reference"></a>select tümcesi (C# Başvurusu)

Bir sorgu ifadesinde `select` yan tümcesi sorgu yürütüldüğünde, üretilecek değerler türünü belirtir. Önceki tümceleri tüm değerlendirmesi ve tüm ifadelerin sonucu dayalı `select` yan tümcesi kendisi. Sorgu ifadesi ile bitmesi bir `select` yan tümcesi veya [grubu](group-clause.md) yan tümcesi.

Aşağıdaki örnek, basit bir gösterir `select` yan tümcesi bir sorgu ifadesinde.

[!code-csharp[cscsrefQueryKeywords#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#8)]  

Sıra türü tarafından üretilen `select` yan tümcesi bir sorgu değişkeni türünü belirler `queryHighScores`. En basit durumda, `select` yan tümcesi yalnızca aralık değişkenini belirtir. Bu veri kaynağı olarak aynı türdeki öğeleri içeren döndürülen dizinin neden olur. Daha fazla bilgi için [LINQ Sorgu işlemlerinde tür ilişkileri](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md). Ancak, `select` yan tümcesi, ayrıca dönüştürme için güçlü bir mekanizma sağlar (veya *planlanması*) yeni tür olarak veri kaynağı. Daha fazla bilgi için [LINQ (C#) ile veri dönüştürmeler](../../programming-guide/concepts/linq/data-transformations-with-linq.md).

## <a name="example"></a>Örnek

Aşağıdaki örnekte tüm farklı formları gösteren bir `select` yan tümcesi alabilir. Her sorgu, arasındaki ilişkiyi unutmayın `select` yan tümcesi ve türünü *sorgu değişkeni* (`studentQuery1`, `studentQuery2`, vb.).

[!code-csharp[cscsrefQueryKeywords#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#9)]

Gösterildiği `studentQuery8` önceki örnekte, bazı durumlarda, yalnızca bir alt kümesini kaynak öğeleri özelliklerini içeren döndürülen dizinin öğelerini isteyebilirsiniz. Döndürülen dizi olabildiğince küçük tutmak tarafından bellek gereksinimlerini azaltın ve sorgu yürütme hızını artırır. İçindeki anonim bir tür oluşturarak bunu gerçekleştirebilirsiniz `select` yan tümcesi ve kaynak öğeden uygun özelliklerle başlatmak için bir nesne Başlatıcı kullanma. Bunu yapmak nasıl bir örnek için bkz [nesne ve koleksiyon başlatıcıları](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).

## <a name="remarks"></a>Açıklamalar

Derleme zamanında `select` yan tümcesi için bir yöntem çağrısına çevrilir <xref:System.Linq.Enumerable.Select%2A> standart sorgu işleci.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [Query Keywords (LINQ)](query-keywords.md)
- [from yan tümcesi](from-clause.md)
- [partial (yöntem) (C# Başvurusu)](partial-method.md)
- [Anonim Tipler](../../programming-guide/classes-and-structs/anonymous-types.md)
- [LINQ Sorgu ifadeleri](../../programming-guide/linq-query-expressions/index.md)
- [C#'de LINQ Kullanmaya Başlama](../../programming-guide/concepts/linq/getting-started-with-linq.md)
