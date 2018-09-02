---
title: select tümcesi (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
ms.openlocfilehash: dcab29cdbe98b5e49463d9a2781d43d4b9ee9544
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467347"
---
# <a name="select-clause-c-reference"></a>select tümcesi (C# Başvurusu)
Bir sorgu ifadesinde `select` yan tümcesi sorgu yürütüldüğünde, üretilecek değerler türünü belirtir. Önceki tümceleri tüm değerlendirmesi ve tüm ifadelerin sonucu dayalı `select` yan tümcesi kendisi. Sorgu ifadesi ile bitmesi bir `select` yan tümcesi veya [grubu](../../../csharp/language-reference/keywords/group-clause.md) yan tümcesi.  
  
 Aşağıdaki örnek, basit bir gösterir `select` yan tümcesi bir sorgu ifadesinde.  
  
 [!code-csharp[cscsrefQueryKeywords#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_1.cs)]  
  
 Sıra türü tarafından üretilen `select` yan tümcesi bir sorgu değişkeni türünü belirler `queryHighScores`. En basit durumda, `select` yan tümcesi yalnızca aralık değişkenini belirtir. Bu veri kaynağı olarak aynı türdeki öğeleri içeren döndürülen dizinin neden olur. Daha fazla bilgi için [LINQ Sorgu işlemlerinde tür ilişkileri](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md). Ancak, `select` yan tümcesi, ayrıca dönüştürme için güçlü bir mekanizma sağlar (veya *planlanması*) yeni tür olarak veri kaynağı. Daha fazla bilgi için [LINQ (C#) ile veri dönüştürmeler](../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte tüm farklı formları gösteren bir `select` yan tümcesi alabilir. Her sorgu, arasındaki ilişkiyi unutmayın `select` yan tümcesi ve türünü *sorgu değişkeni* (`studentQuery1`, `studentQuery2`, vb.).  
  
 [!code-csharp[cscsrefQueryKeywords#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_2.cs)]  
  
 Gösterildiği `studentQuery8` önceki örnekte, bazı durumlarda, yalnızca bir alt kümesini kaynak öğeleri özelliklerini içeren döndürülen dizinin öğelerini isteyebilirsiniz. Döndürülen dizi olabildiğince küçük tutmak tarafından bellek gereksinimlerini azaltın ve sorgu yürütme hızını artırır. İçindeki anonim bir tür oluşturarak bunu gerçekleştirebilirsiniz `select` yan tümcesi ve kaynak öğeden uygun özelliklerle başlatmak için bir nesne Başlatıcı kullanma. Bunu yapmak nasıl bir örnek için bkz [nesne ve koleksiyon başlatıcıları](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
## <a name="remarks"></a>Açıklamalar  
 Derleme zamanında `select` yan tümcesi için bir yöntem çağrısına çevrilir <xref:System.Linq.Enumerable.Select%2A> standart sorgu işleci.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [Sorgu anahtar sözcükleri (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
- [from yan tümcesi](../../../csharp/language-reference/keywords/from-clause.md)  
- [partial (yöntem) (C# Başvurusu)](../../../csharp/language-reference/keywords/partial-method.md)  
- [Anonim Tipler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
- [LINQ Sorgu ifadeleri](../../../csharp/programming-guide/linq-query-expressions/index.md)  
- [C#'de LINQ Kullanmaya Başlama](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
