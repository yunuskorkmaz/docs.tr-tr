---
title: where yan tümcesi - C# Referans
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: 33616e4eacb484b9c6eda3862cd86fdd1e6df165
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173490"
---
# <a name="where-clause-c-reference"></a>where tümcesi (C# Başvurusu)

Yan `where` tümce, sorgu ifadesinde veri kaynağından hangi öğelerin döndürüleceğini belirtmek için bir sorgu ifadesinde kullanılır. Her kaynak öğe öğesine (aralık değişkeni tarafından başvurulan) boolean koşulu *(yüklem)* uygular ve belirtilen koşulun doğru olduğu durumu döndürür. Tek bir sorgu ifadesi `where` birden çok yan tümce içerebilir ve tek bir yan tümce birden çok yüklem alt ifadesi içerebilir.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, `where` yan tümce beşten küçük olanlar dışındaki tüm sayıları filtreler. Yan tümceyi `where` kaldırırsanız, veri kaynağından tüm sayılar döndürülür. İfade, `num < 5` her öğeye uygulanan yüklemdir.

[!code-csharp[cscsrefQueryKeywords#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#5)]

## <a name="example"></a>Örnek

Tek `where` bir yan tümce içinde, ve [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) işleçleri [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) kullanarak gerektiği kadar yüklem belirtebilirsiniz. Aşağıdaki örnekte, sorgu yalnızca beşten küçük olan çift sayıları seçmek için iki yüklem belirtir.

[!code-csharp[cscsrefQueryKeywords#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#6)]  

## <a name="example"></a>Örnek

Bir `where` yan tümce Boolean değerlerini döndüren bir veya daha fazla yöntem içerebilir. Aşağıdaki örnekte, `where` yan tümce, aralık değişkeninin geçerli değerinin çift veya tek olup olmadığını belirlemek için bir yöntem kullanır.

[!code-csharp[cscsrefQueryKeywords#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#7)]

## <a name="remarks"></a>Açıklamalar

Yan `where` tümce bir filtreleme mekanizmasıdır. İlk veya son tümce olamaz dışında, sorgu ifadesinde hemen hemen her yerde konumlandırılabilir. Bir `where` yan tümce, gruplandırılmadan önce veya sonra kaynak öğeleri filtrelemeniz gerekip gerekmediğine bağlı olarak [bir grup](group-clause.md) yan tümcesinden önce veya sonra görünebilir.

Veri kaynağındaki öğeler için belirli bir yüklem geçerli değilse, derleme zamanı hatası oluşur. Bu, LINQ tarafından sağlanan güçlü tür denetiminin bir avantajıdır.

Derleme zamanında `where` anahtar <xref:System.Linq.Enumerable.Where%2A> kelime, Standart Sorgu Operatörü yöntemine çağrıya dönüştürülür.

## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Anahtar Kelimeleri (LINQ)](query-keywords.md)
- [fıkradan](from-clause.md)
- [yan tümceyi seçin](select-clause.md)
- [Verileri filtreleme](../../programming-guide/concepts/linq/filtering-data.md)
- [C# üzerinde LINQ](../../linq/index.md)
- [Dil ile Tümleşik Sorgu (LINQ)](../../programming-guide/concepts/linq/index.md)
