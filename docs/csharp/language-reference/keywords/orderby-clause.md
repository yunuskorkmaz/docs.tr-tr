---
description: OrderBy tümcesi-C# başvurusu
title: OrderBy tümcesi-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: 2f64b45ff252c7cc02e56c465da21ccc5e861aec
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142355"
---
# <a name="orderby-clause-c-reference"></a>orderby tümcesi (C# Başvurusu)

Bir sorgu ifadesinde `orderby` yan tümce döndürülen sıranın veya alt dizinin (Grup) artan veya azalan sırada sıralanmasını sağlar. Bir veya daha fazla ikincil sıralama işlemi gerçekleştirmek için birden çok anahtar belirtilebilir. Sıralama, öğe türü için varsayılan karşılaştırıcı tarafından gerçekleştirilir. Varsayılan sıralama düzeni artan. Ayrıca, özel bir karşılaştırıcı da belirtebilirsiniz. Ancak, yalnızca Yöntem tabanlı sözdizimi kullanılarak kullanılabilir. Daha fazla bilgi için bkz. [verileri sıralama](../../programming-guide/concepts/linq/sorting-data.md).

## <a name="example"></a>Örnek

Aşağıdaki örnekte, ilk sorgu kelimeleri bir ' dan başlayarak alfabetik sırada sıralar ve ikinci sorgu aynı sözcükleri azalan düzende sıralar. ( `ascending` Anahtar sözcüğü varsayılan sıralama değeridir ve atlanabilir.)

[!code-csharp[cscsrefQueryKeywords#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#20)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, öğrencilerin soyadı üzerinde birincil bir sıralama ve ardından ilk adlarında ikinci bir sıralama gerçekleştirir.

[!code-csharp[cscsrefQueryKeywords#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#22)]

## <a name="remarks"></a>Açıklamalar

Derleme zamanında `orderby` yan tümce yöntemine bir çağrıya çevrilir <xref:System.Linq.Enumerable.OrderBy%2A> . Yan tümcesindeki birden çok anahtar `orderby` <xref:System.Linq.Enumerable.ThenBy%2A> metot çağrılarına çeviri yapar.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [Sorgu anahtar sözcükleri (LINQ)](query-keywords.md)
- [C# üzerinde LINQ](../../linq/index.md)
- [group tümcesi](group-clause.md)
- [Dil ile Tümleşik Sorgu (LINQ)](../../programming-guide/concepts/linq/index.md)
