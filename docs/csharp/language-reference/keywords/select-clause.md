---
title: select yan tümcesi - C# Reference
ms.date: 07/20/2015
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
ms.openlocfilehash: 68ea7ad6fc7cf5580dbdd0ae7f012f36566db0dc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173516"
---
# <a name="select-clause-c-reference"></a>select tümcesi (C# Başvurusu)

Sorgu ifadesinde, `select` tümce, sorgu yürütüldüğünde üretilecek değerlerin türünü belirtir. Sonuç, önceki tüm yan tümmaddelerin değerlendirilmesini ve tümcenin `select` kendisindeki tüm ifadelere dayanır. Sorgu ifadesi, bir `select` yan tümce veya [grup](group-clause.md) yan tümcesi ile sonlandırılmalıdır.

Aşağıdaki örnekte, `select` sorgu ifadesinde basit bir yan tümce gösterilmektedir.

[!code-csharp[cscsrefQueryKeywords#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#8)]  

`select` Yan tümcetarafından üretilen sıranın türü sorgu değişkeninin `queryHighScores`türünü belirler. En basit durumda, `select` yan tümce sadece aralık değişkenini belirtir. Bu, döndürülen dizinin veri kaynağıyla aynı türden öğeleri içermesine neden olur. Daha fazla bilgi için [LINQ Sorgu İşlemlerinde Tür İlişkileri'ne](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)bakın. Ancak, `select` yan tümce, kaynak verileri yeni türlere dönüştürmek (veya *yansıtmak)* için güçlü bir mekanizma da sağlar. Daha fazla bilgi için [LINQ (C#) ile Veri Dönüşümleri'ne](../../programming-guide/concepts/linq/data-transformations-with-linq.md)bakın.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir `select` yan tümcenin alabilecekleri tüm farklı formları gösterir. Her `select` sorguda, yan tümce ile sorgu *değişkeninin* türü (`studentQuery1`, , `studentQuery2`vb.) arasındaki ilişkiyi not edin.

[!code-csharp[cscsrefQueryKeywords#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#9)]

Önceki örnekte `studentQuery8` gösterildiği gibi, bazen döndürülen dizinin öğelerinin yalnızca kaynak öğelerin özelliklerinin bir alt kümesini içermesini isteyebilirsiniz. Döndürülen sırayı mümkün olduğunca küçük tutarak bellek gereksinimlerini azaltabilir ve sorgunun yürütme hızını artırabilirsiniz. Bunu, `select` yan tümcede anonim bir tür oluşturarak ve kaynak öğeden uygun özelliklerle başlatılması için bir nesne baş harflerini kullanarak gerçekleştirebilirsiniz. Bunun nasıl yapılacağının bir örneği için [Object ve Collection Initializers](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)bölümüne bakın.

## <a name="remarks"></a>Açıklamalar

Derleme zamanında, `select` yan tümce <xref:System.Linq.Enumerable.Select%2A> standart sorgu işleciiçin bir yöntem çağrısına çevrilir.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [Sorgu Anahtar Kelimeleri (LINQ)](query-keywords.md)
- [fıkradan](from-clause.md)
- [kısmi (Yöntem) (C# Referans)](partial-method.md)
- [Anonim Türler](../../programming-guide/classes-and-structs/anonymous-types.md)
- [C# üzerinde LINQ](../../linq/index.md)
- [Dil ile Tümleşik Sorgu (LINQ)](../../programming-guide/concepts/linq/index.md)
