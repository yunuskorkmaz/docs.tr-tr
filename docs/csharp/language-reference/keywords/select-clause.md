---
description: Select yan tümcesi-C# başvurusu
title: Select yan tümcesi-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
ms.openlocfilehash: d67c99cc841c08a63cc83843a07a46e80199b9d1
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89136908"
---
# <a name="select-clause-c-reference"></a>select tümcesi (C# Başvurusu)

Bir sorgu ifadesinde `select` yan tümce, sorgu yürütüldüğünde üretilecek değerlerin türünü belirtir. Sonuç, tüm önceki yan tümcelerin ve yan tümcedeki herhangi bir ifadenin değerlendirmesine dayanır `select` . Sorgu ifadesinin bir `select` yan tümce veya bir [Grup](group-clause.md) yan tümcesiyle sonlandırılması gerekir.

Aşağıdaki örnekte bir `select` sorgu ifadesinde basit bir yan tümce gösterilmektedir.

[!code-csharp[cscsrefQueryKeywords#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#8)]  

Yan tümce tarafından üretilen sıranın türü, `select` sorgu değişkeninin türünü belirler `queryHighScores` . En basit durumda, `select` yan tümce yalnızca Aralık değişkenini belirtir. Bu, döndürülen sıranın veri kaynağıyla aynı türdeki öğeleri içermesini sağlar. Daha fazla bilgi için bkz. [LINQ sorgu Işlemlerinde tür ilişkileri](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md). Ancak `select` yan tümce, kaynak verilerini yeni türlere dönüştürmek (veya *yansıtma*) için güçlü bir mekanizma sağlar. Daha fazla bilgi için bkz. [LINQ Ile veri dönüştürmeleri (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir `select` yan tümcesinin götüreolabileceği tüm farklı formları gösterir. Her sorguda, `select` yan tümcesi ve *sorgu değişkeninin* türü ( `studentQuery1` ,, vb.) arasındaki ilişkiyi aklınızda yazın `studentQuery2` .

[!code-csharp[cscsrefQueryKeywords#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#9)]

`studentQuery8`Önceki örnekte gösterildiği gibi, bazen döndürülen dizideki öğelerin yalnızca kaynak öğelerin özelliklerinin bir alt kümesini içermesini isteyebilirsiniz. Döndürülen sırayı mümkün olduğunca küçük tutarak, bellek gereksinimlerini azaltabilir ve sorgunun yürütme hızını artırabilirsiniz. Bunu, yan tümcesinde anonim bir tür oluşturarak `select` ve kaynak öğeden uygun özelliklerle başlatmak için bir nesne Başlatıcısı kullanarak yapabilirsiniz. Bunun nasıl yapılacağı hakkında bir örnek için bkz. [nesne ve koleksiyon başlatıcıları](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).

## <a name="remarks"></a>Açıklamalar

Derleme zamanında `select` yan tümce <xref:System.Linq.Enumerable.Select%2A> Standart sorgu işlecine bir yöntem çağrısına çevrilir.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [Sorgu anahtar sözcükleri (LINQ)](query-keywords.md)
- [from tümcesi](from-clause.md)
- [partial (Yöntem) (C# Başvurusu)](partial-method.md)
- [Anonim Türler](../../programming-guide/classes-and-structs/anonymous-types.md)
- [C# üzerinde LINQ](../../linq/index.md)
- [Dil ile Tümleşik Sorgu (LINQ)](../../programming-guide/concepts/linq/index.md)
