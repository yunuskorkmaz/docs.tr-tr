---
title: Burada yan tümcesi - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: 470fcfde7a5e68887fa3a6e99cb8881073ffeba5
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59341393"
---
# <a name="where-clause-c-reference"></a>where tümcesi (C# Başvurusu)

`where` Yan tümcesi bir sorgu ifadesinde sorgu ifadesi içinde veri kaynağından hangi öğelerin döndürülmesi belirtmek için kullanılır. Bir Boolean koşulu uygular (*koşul*) için her kaynak öğesi (aralık değişkeni tarafından başvurulan) ve bunlar için belirtilen koşulun true döndürür. Tek bir sorgu ifadesi birden çok içerebilir `where` yan tümceleri ve tek bir yan tümce birden çok koşul alt ifadeler içeriyor olabilir.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, `where` yan tümcesi filtreler en az beş olanlar dışındaki tüm sayılar uğradı. Kaldırırsanız `where` yan tümcesi, veri kaynağından tüm sayılar döndürülen. İfade `num < 5` her öğeye uygulanan koşuldur.

[!code-csharp[cscsrefQueryKeywords#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#5)]

## <a name="example"></a>Örnek

Tek bir `where` yan tümcesini kullanarak, çok doğrulamaları gerektiği gibi belirtebilirsiniz [ && ](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) ve [ &#124; &#124; ](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) işleçleri. Aşağıdaki örnekte, yalnızca en az beş olan çift sayıları seçmek için iki doğrulamaları sorguyu belirtir.

[!code-csharp[cscsrefQueryKeywords#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#6)]  

## <a name="example"></a>Örnek

A `where` yan tümcesi, Boole değerleri döndüren bir veya daha fazla yöntemler içerebilir. Aşağıdaki örnekte, `where` yan tümcesinin Aralık değişkeninin geçerli değerini çift veya tek sayı olup olmadığını belirlemek için bir yöntem kullanır.

[!code-csharp[cscsrefQueryKeywords#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#7)]

## <a name="remarks"></a>Açıklamalar

`where` Yan tümcesi ise bir filtreleme mekanizması. İlk veya son yan tümcesi olamaz dışında bir sorgu ifadesinde, neredeyse her yerden konumlandırılmalıdır. A `where` yan tümcesi, önce veya sonra görünebilir bir [grubu](group-clause.md) önce veya sonra gruplanmış olan kaynak öğeleri filtrelemek olmasına bağlı olarak yan tümcesi.

Belirtilen bir koşulu veri kaynağındaki öğeleri için geçerli değilse, bir derleme zamanı hatası neden olur. Bu güçlü tür tarafından sağlanan denetimi bir yararı, [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].

Derleme zamanında `where` anahtar sözcüğü, bir çağrı biçimine dönüştürülür <xref:System.Linq.Enumerable.Where%2A> standart sorgu işleci yöntem.

## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Anahtar Sözcükleri (LINQ)](query-keywords.md)
- [from yan tümcesi](from-clause.md)
- [select tümcesi](select-clause.md)
- [Verileri Filtreleme](../../programming-guide/concepts/linq/filtering-data.md)
- [LINQ Sorgu İfadeleri](../../../csharp/programming-guide/linq-query-expressions/index.md)
- [C#'de LINQ'e Başlarken](../../programming-guide/concepts/linq/getting-started-with-linq.md)