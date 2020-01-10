---
title: Select yan tümcesi C# -başvuru
ms.date: 07/20/2015
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
ms.openlocfilehash: b4d25f80e4cdb08fbc28fa4db3cb1c790b1145e6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713098"
---
# <a name="select-clause-c-reference"></a>select tümcesi (C# Başvurusu)

Sorgu ifadesinde `select` yan tümcesi, sorgu yürütüldüğünde üretilecek değerlerin türünü belirtir. Sonuç, tüm önceki yan tümcelerinin ve `select` yan tümcesinin içindeki herhangi bir ifadenin değerlendirmesine dayanır. Sorgu ifadesinin bir `select` yan tümcesiyle veya bir [Grup](group-clause.md) yan tümcesiyle sonlandırılması gerekir.

Aşağıdaki örnekte, bir sorgu ifadesinde basit bir `select` yan tümcesi gösterilmektedir.

[!code-csharp[cscsrefQueryKeywords#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#8)]  

`select` yan tümcesi tarafından üretilen sıranın türü, `queryHighScores`sorgu değişkeninin türünü belirler. En basit durumda, `select` yan tümcesi yalnızca Aralık değişkenini belirtir. Bu, döndürülen sıranın veri kaynağıyla aynı türdeki öğeleri içermesini sağlar. Daha fazla bilgi için bkz. [LINQ sorgu Işlemlerinde tür ilişkileri](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md). Ancak `select` yan tümcesi, kaynak verilerini yeni türlere dönüştürmek (veya *yansıtma*) için güçlü bir mekanizma sağlar. Daha fazla bilgi için bkz. [LINQ (C#) ile veri dönüştürmeleri](../../programming-guide/concepts/linq/data-transformations-with-linq.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir `select` yan tümcesinin götüreolabileceği tüm farklı formları gösterir. Her sorguda `select` yan tümcesi ve *sorgu değişkeninin* türü (`studentQuery1`, `studentQuery2`, vb.) arasındaki ilişkiyi aklınızda yazın.

[!code-csharp[cscsrefQueryKeywords#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#9)]

Önceki örnekte `studentQuery8` gösterildiği gibi, bazen döndürülen dizideki öğelerin yalnızca kaynak öğelerin özelliklerinin bir alt kümesini içermesini isteyebilirsiniz. Döndürülen sırayı mümkün olduğunca küçük tutarak, bellek gereksinimlerini azaltabilir ve sorgunun yürütme hızını artırabilirsiniz. Bunu, `select` yan tümcesinde anonim bir tür oluşturarak ve kaynak öğeden uygun özelliklerle başlatmak için bir nesne Başlatıcısı kullanarak yapabilirsiniz. Bunun nasıl yapılacağı hakkında bir örnek için bkz. [nesne ve koleksiyon başlatıcıları](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).

## <a name="remarks"></a>Açıklamalar

Derleme zamanında, `select` yan tümcesi <xref:System.Linq.Enumerable.Select%2A> standart sorgu işlecine bir yöntem çağrısına çevrilir.

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [Sorgu anahtar sözcükleri (LINQ)](query-keywords.md)
- [from yan tümcesi](from-clause.md)
- [partial (Yöntem) (C# başvuru)](partial-method.md)
- [Anonim Tipler](../../programming-guide/classes-and-structs/anonymous-types.md)
- [C# üzerinde LINQ](../../linq/index.md)
- [C#'de LINQ Kullanmaya Başlama](/dotnet/csharp/programming-guide/concepts/linq/)
